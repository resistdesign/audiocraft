# audiocraft
FB AudioCraft w/ Gradio

```Dockerfile
# Use an official Python runtime as a parent image
FROM python:3.9-slim-buster

# Install some base utilities
RUN apt-get update && apt-get install -y \
    git \
    software-properties-common \
    curl

# Installing ffmpeg via apt-get
RUN apt-get update && apt-get install -y ffmpeg

# Set the working directory in the container
WORKDIR /usr/src/app

# Clone the Audiocraft repository
RUN git clone https://github.com/facebookresearch/audiocraft.git

# Change to the Audiocraft directory
WORKDIR /usr/src/app/audiocraft

# Install PyTorch and Audiocraft
RUN pip install 'torch>=2.0' && pip install -U audiocraft

# Install other requirements
RUN pip install -r requirements.txt

# Run the musicgen_app demo
CMD ["python", "-m", "demos.musicgen_app", "--share"]
```
