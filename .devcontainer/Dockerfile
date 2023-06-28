# adapted from https://github.com/devcontainers/images/blob/main/src/cpp/.devcontainer/Dockerfile

# [Choice] Debian / Ubuntu version (use Debian 12, Debian 11, Ubuntu 22.04 on local arm64/Apple Silicon): debian-12, debian-11, debian-10, ubuntu-22.04, ubuntu-20.04
ARG VARIANT=ubuntu-22.04
FROM mcr.microsoft.com/devcontainers/base:${VARIANT}
USER root

# Install needed packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install build-essential cmake cppcheck valgrind clang lldb llvm gdb \
    && apt-get autoremove -y && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Installing Arm GCC from https://github.com/carlosperate/docker-microbit-toolchain/blob/master/Dockerfile 
WORKDIR /opt/
RUN cd /opt/ && \
    wget -q https://developer.arm.com/-/media/Files/downloads/gnu-rm/10-2020q4/gcc-arm-none-eabi-10-2020-q4-major-x86_64-linux.tar.bz2 && \
    echo "8312c4c91799885f222f663fc81f9a31  gcc-arm-none-eabi-10-2020-q4-major-x86_64-linux.tar.bz2" >> MD5SUM && \
    md5sum -c MD5SUM && \
    rm MD5SUM && \
    tar -xf gcc-arm-none-eabi-10-2020-q4-major-x86_64-linux.tar.bz2 && \
    rm gcc-arm-none-eabi-10-2020-q4-major-x86_64-linux.tar.bz2
ENV PATH $PATH:/opt/gcc-arm-none-eabi-10-2020-q4-major/bin