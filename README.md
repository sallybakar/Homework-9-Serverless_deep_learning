Homework 9: Serverless Deep Learning
This project demonstrates steps to develop and deploy a TensorFlow Lite model for serverless environments using Docker and AWS Lambda. The tasks involve model conversion, data preprocessing, Docker setup, and Lambda deployment.

Key Features
Model Conversion: Convert a Keras model to TensorFlow Lite format.
Data Preparation: Preprocess images for model inference.
Docker Integration: Set up a Docker environment for TensorFlow Lite runtime.
AWS Lambda Deployment: Package and deploy the model for serverless inference.
Prerequisites
Before starting, ensure you have the following installed:

Python 3.10
TensorFlow >= 2.14.0
Pillow for image processing
Docker for creating and running containerized applications
AWS CLI for Lambda deployment
Getting Started
1. Clone the Repository
bash
Copy code
git clone <repository-link>
cd <repository-folder>
2. Install Dependencies
Install the required Python libraries:

bash
Copy code
pip install tensorflow pillow numpy==1.23.1
3. Convert Keras Model to TensorFlow Lite
Follow the steps in the notebook to convert the Keras model:

Export the Keras model.
Convert it using TensorFlow Lite tools.
4. Prepare Docker Image
Use the provided Dockerfile:

Dockerfile
Copy code
FROM public.ecr.aws/lambda/python:3.10

COPY model.tflite . 

RUN pip install numpy==1.23.1
Build and test the Docker image:

bash
Copy code
docker build -t serverless-tflite .
docker run --rm serverless-tflite
5. Deploy to AWS Lambda
Package the Docker image and push it to AWS ECR:

bash
Copy code
aws ecr create-repository --repository-name serverless-tflite
docker tag serverless-tflite:latest <ecr-repo-uri>:latest
docker push <ecr-repo-uri>:latest
Deploy the image to AWS Lambda using the AWS Management Console or CLI.

Notable Resources
TensorFlow Lite Documentation
Docker Official Documentation
AWS Lambda Documentation
