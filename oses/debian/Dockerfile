FROM        --platform=$TARGETOS/$TARGETARCH debian:bookworm-slim

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

LABEL       org.opencontainers.image.source="https://github.com/pterodactyl/yolks"
LABEL       org.opencontainers.image.licenses=MIT
RUN 		dpkg --add-architecture i386

RUN         apt update && apt upgrade -y \
				&& apt install -y gcc curl libcurl4:i386 g++ libgcc1 libc++-dev libstdc++6:i386 gdb libc6 git wget curl tar zip unzip binutils xz-utils liblzo2-2 cabextract iproute2 net-tools netcat-traditional telnet libatomic1 libsdl1.2debian libsdl2-2.0-0 \
    			libfontconfig libicu-dev icu-devtools libunwind8 libssl-dev sqlite3 libsqlite3-dev libmariadb-dev duktape locales ffmpeg gnupg2 apt-transport-https software-properties-common ca-certificates tzdata \
    			liblua5.3-0 libz-dev rapidjson-dev \
				&& update-locale lang=en_US.UTF-8 \
				&& dpkg-reconfigure --frontend noninteractive locales \
				&& useradd -m -d /home/container -s /bin/bash container

USER        container
ENV         USER=container HOME=/home/container
ENV         DEBIAN_FRONTEND noninteractive

WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]