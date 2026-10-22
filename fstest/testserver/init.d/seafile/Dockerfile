ARG SEAFILE_VERSION=latest
FROM seafileltd/seafile-mc:${SEAFILE_VERSION}

# The upstream Seafile image bundles nginx 1.26.2. Upgrade its signed package
# while preserving Seafile's custom nginx.conf and the application's entrypoint.
RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y --only-upgrade \
      -o Dpkg::Options::=--force-confold nginx \
 && dpkg --compare-versions "$(dpkg-query -W -f='${Version}' nginx)" ge "1.30.6-1~jammy" \
 && rm -rf /var/lib/apt/lists/*
