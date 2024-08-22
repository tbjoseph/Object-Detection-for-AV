## Overview
Our system leverages advanced computer vision and machine learning techniques to perform image segmentation, depth estimation, and object detection in a 3D environment. The software is structured into three primary components, each responsible for a different aspect of the processing pipeline, running on an Orin Nano with Ubuntu. The system is designed for real-time application, with emphasis on speed and efficiency on constrained hardware.

## System Components

Object Detection and Segmentation:
* Model: YOLOv8n-seg from Ultralytics, optimized for performance with 3.4M parameters.
* Libraries: Pytorch, Torchvision, Ultralytics (CUDA-enabled for GPU utilization).
* Function: Processes frames from an external camera to output class labels and segmentation masks for each detected object.

Depth Estimation:
* Approach: Custom algorithm using the camera’s vertical and horizontal FOV.
* Technology: Implemented in Python, it estimates the distance of objects from the camera using trigonometric calculations.

3D Environment Mapping:
* Tools: NumPy for numerical computations and PyOpenGL for rendering 3D graphics.
* Process: Integrates data from the segmentation model and depth estimation to compute distances and velocities, rendering this information onto an external display.

## Specifications
YOLOv8n-seg Performance:
* Size: 640 pixels
* Speed on A100 TensorRT: 1.21 ms
* Parameters: 3.4M
* FLOPs: 12.6B

## Installation
* Operating System: Ubuntu on Orin Nano, accessible via SSH.
* Python Version: 3.8 or 3.9.
* Dependencies: Install CUDA toolkit on the Orin Nano for GPU support.
* Python Libraries: Ensure versions of Pytorch, Torchvision, Ultralytics, OpenCV, NumPy, and PyOpenGL are installed and compatible with CUDA.

## Usage
* Frame Capture: Utilize OpenCV to capture frames from the external camera in a format compatible with YOLOv8.
* Run Detection and Segmentation: Execute the Python script that incorporates the yolov8n-seg model to process images.
* Depth and 3D Mapping: The custom depth algorithm and 3D mapping scripts compute and visualize the environment based on the data received.
