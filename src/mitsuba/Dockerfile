# syntax=docker/dockerfile:1.4

# Base Image
# =============================================================================
# Use an Ubuntu base image
FROM ubuntu:20.04

# Set environment variables to avoid user interaction during installation
ENV DEBIAN_FRONTEND=noninteractive

# Update and install dependencies
RUN apt-get update && apt-get install -y \
    git \
    cmake \
    build-essential \
    python3 \
    python3-pip \
    libtbb-dev \
    libeigen3-dev \
    libpng-dev \
    libjpeg-dev \
    libxerces-c-dev \
    libglew-dev \
    libglfw3-dev \
    libopenexr-dev \
    libbz2-dev \
    liblzma-dev

# Clone Mitsuba's repository
RUN git clone --recursive https://github.com/mitsuba-renderer/mitsuba.git

# Build Mitsuba
WORKDIR /mitsuba
RUN mkdir build
WORKDIR /mitsuba/build
RUN cmake ..
RUN make -j4

# Set up environment variables for Mitsuba
ENV MITSUBA_DIR /mitsuba
ENV PATH="${MITSUBA_DIR}:${PATH}"

# Set the default command
CMD ["mitsuba"]

