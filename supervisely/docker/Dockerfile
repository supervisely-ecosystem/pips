FROM nvidia/cuda:11.8.0-runtime-ubuntu20.04
ENV TZ="Europe/Tallinn"
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
   python3 \
   python3-pip \
   ffmpeg libsm6 libxext6 \
   git \
   wget \
   && rm -rf /var/lib/apt/lists/*

RUN mkdir /weights
RUN cd /weights && wget --no-check-certificate 'https://github.com/supervisely-ecosystem/pips/releases/download/v0.0.1/model-000200000.pth' -O model-000200000.pth

RUN apt update && apt install -y python-is-python3
ENV WEIGHTS_DIR="/weights"


RUN pip3 install --no-cache-dir torch==2.0.0 torchvision==0.15.1 --index-url https://download.pytorch.org/whl/cu121

RUN pip3 install --no-cache-dir imageio==2.19.3 \
   opencv-python==4.6.0.66 \
   tensorboardX==2.2 \
   einops==0.4.1 \
   scikit-learn==1.1.1 \
   matplotlib==3.5.1 \
   protobuf==3.20.0 \
   fire==0.4.0 \
   moviepy==1.0.3 \
   urllib3==1.26.15

RUN pip3 install --no-cache-dir supervisely==6.73.486

LABEL python_sdk_version="6.73.486"
