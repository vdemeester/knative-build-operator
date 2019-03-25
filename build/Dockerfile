FROM registry.access.redhat.com/ubi7-dev-preview/ubi-minimal:7.6

ARG version

ENV OPERATOR=/usr/local/bin/knative-build-operator \
    USER_UID=1001 \
    USER_NAME=knative-build-operator \
    RESOURCE_VERSION=$version

# install operator binary
COPY build/_output/bin/knative-build-operator ${OPERATOR}

COPY build/bin /usr/local/bin
RUN  /usr/local/bin/user_setup

# install manifest[s]
COPY deploy /deploy

ENTRYPOINT ["/usr/local/bin/entrypoint"]

USER ${USER_UID}
