# Gesture-Recognition
Gesture Recognition for Consumer electronics - Smart TV

### Problem Statement

A home electronics company which manufactures state of the art smart televisions want to develop a cool feature in the smart-TV that can recognise five different gestures performed by the user which will help users control the TV without using a remote. Let's have professor Raghavan introduce you to the problem statement:

The gestures are continuously monitored by the webcam mounted on the TV. Each gesture corresponds to a specific command:

Thumbs up:  Increase the volume
Thumbs down: Decrease the volume
Left swipe: 'Jump' backwards 10 seconds
Right swipe: 'Jump' forward 10 seconds  
Stop: Pause the movie

Each video is a sequence of 30 frames (or images).

### Understanding the Dataset

The training data consists of a few hundred videos categorised into one of the five classes. Each video (typically 2-3 seconds long) is divided into a sequence of 30 frames(images). These videos have been recorded by various people performing one of the five gestures in front of a webcam - similar to what the smart TV will use. 

The data is in a zip file. The zip file contains a 'train' and a 'val' folder with two CSV files for the two folders. These folders are in turn divided into subfolders where each subfolder represents a video of a particular gesture. Each subfolder, i.e. a video, contains 30 frames (or images). Note that all images in a particular video subfolder have the same dimensions but different videos may have different dimensions. Specifically, videos have two types of dimensions - either 360x360 or 120x160 (depending on the webcam used to record the videos). Hence, you will need to do some pre-processing to standardise the videos. 

Each row of the CSV file represents one video and contains three main pieces of information - the name of the subfolder containing the 30 images of the video, the name of the gesture and the numeric label (between 0-4) of the video.

### Architecture

For analysing videos using neural networks, two types of architectures are used commonly. 

1. Standard CNN + RNN architecture - The conv2D network will extract a feature vector for each image, and a sequence of these feature vectors is then fed to an RNN-based network. The output of the RNN is a regular softmax (for a classification problem such as this one).

2. 3D convolutional network - Just like in 2D conv, you move the filter in two directions (x and y), in 3D conv, you move the filter in three directions (x, y and z). In this case, the input to a 3D conv is a video (which is a sequence of 30 RGB images). If we assume that the shape of each image is 100x100x3, for example, the video becomes a 4-D tensor of shape 100x100x3x30 which can be written as (100x100x30)x3 where 3 is the number of channels. 

We will be deriving best model by trying out both of the architectures.

### Analysis

We will be using Keras API with TensorFlow backend.

- Reading the Images folder
- Preprocessing the Images - Crop, Resize, Standardize
- Data Augmentation if required
- Choosing Appropriate Batch size, Number of epochs,Image size, Number of required frames in a video.
- Creating Custom Generator Function
- Applying various models - Conv2D+LSTM, Conv2D+GRU, Conv3D

### Conclusion

Conv2D+LSTM  model gave Training accuracy of 0.79 and Validation Accuracy of 0.76 which is close and indicates a good trained model. Since training accuracy and validation accuracy are nearby this model is not overfitting.
Hence, we are choosing ConvLSTM to be the final model.
















