ARG BUILD_FROM
ARG NEOHUB_IMAGE

FROM ${NEOHUB_IMAGE} AS neohub-source

FROM ${BUILD_FROM}

COPY --from=neohub-source /usr/share/dotnet /usr/share/dotnet
COPY --from=neohub-source /app /app

RUN ln -s /usr/share/dotnet/dotnet /usr/bin/dotnet

ENV NEOHUB_PERSIST_PATH=/config \
    DOTNET_SYSTEM_GLOBALIZATION_INVARIANT=1

WORKDIR /app

COPY rootfs /
RUN chmod a+x /etc/s6-overlay/s6-rc.d/neohub/run
