# Runtime image for the supabase/vector fork. The build context is a staged
# rootfs (see .github/workflows/supabase_ghcr.yml) holding a natively built
# binary laid out like the upstream .deb package.
FROM docker.io/debian:trixie-slim@sha256:a72b4433de1cf7d6bae0c4cee74d0547f58601a643b3375f070c51600d63b6b2

LABEL org.opencontainers.image.url="https://vector.dev"
LABEL org.opencontainers.image.source="https://github.com/supabase/vector"
LABEL org.opencontainers.image.documentation="https://vector.dev/docs"

# hadolint ignore=DL3008
RUN apt-get update && apt-get install -y --no-install-recommends ca-certificates tzdata systemd libsasl2-2 && rm -rf /var/lib/apt/lists/*

COPY rootfs/ /

# Smoke test
RUN ["vector", "--version"]

ENTRYPOINT ["/usr/bin/vector"]
