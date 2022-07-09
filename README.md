# INTRODUCTION
Image segmentation is the process of partitioning a digital image into multiple image segments, also known as image regions or image objects (sets of pixels). The goal of segmentation is to simplify and/or change the representation of an image into something that is more meaningful and easier to analyze. Image segmentation is typically used to locate objects and boundaries (lines, curves, etc.) in images. More precisely, image segmentation is the process of assigning a label to every pixel in an image such that pixels with the same label share certain characteristics. Image segmentation results in more granular information about the shape of an image and thus an extension of the concept of Object Detection.

We segment i.e. divide the images into regions of different colors which helps in distinguishing an object from the other at a finer level.

# LIST OF LIBRARIES USED:
- numpy
- scipy
- pillow
- cython
- matplotlib
- scikit-image
- tensorflow
- keras
- opencv-python
- h5py
- imgaug
- ipython

# METHODOLOGY
We are going to perform image segmentation using the Mask R-CNN architecture. It is an extension of the Faster R-CNN Model which is preferred for object detection tasks.

The Mask R-CNN returns the binary object mask in addition to class label and object bounding box. Mask R-CNN is good at pixel level segmentation.
We utilize the ResNet 101 architecture to extract features from the input image. As a result, we get feature maps which are transmitted to Region Proposed Network
After obtaining the feature maps, bounding box candidates are determined and thus RPN extracts RoI (Region of Interest)
Faster R-CNN uses an RoI Pool layer to compute features from the obtained proposals in order to infer the class of the object and bounding box coordinates.
RoI pool led to misalignments in getting the Region of Interest due to quantization of RoI coordinates. Since pixel-level segmentation required specificity hence authors of the Faster R-CNN cleverly solved it by implementing the RoI Align.

Inferencing the MASK R-CNN extracts the features of image:
![RESULT 1](https://user-images.githubusercontent.com/83603244/178092253-68e80fea-a3cc-4ac5-b9f4-68d02c5b2208.jpg)

Next important thing to observe here is the mask shape which is 28×28 as it is trained on the COCO dataset and we have a total of 81 classes.

This means that there are 81 possible prediction classes in which an object may fall into.
