# Use the official Python dockimg as the base dockimg
FROM nvidia/cuda:12.1.0-base-ubuntu22.04

# Install software required for Python3
RUN apt update && apt install python3 python3-pip -y
# Install software required for OpenCV to work
RUN apt update && apt install ffmpeg libsm6 libxext6  -y
# Install software curl, ping, lspci
RUN apt update && apt install curl inetutils-ping pciutils -y

# Set the working directory inside the container
WORKDIR /app

COPY requirements.txt .

# Install any dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the FastAPI application code to the container
COPY . .

# YOLO model convert TensorRT
# Command to run the FastAPI application using Uvicorn
CMD ["./run.sh"]