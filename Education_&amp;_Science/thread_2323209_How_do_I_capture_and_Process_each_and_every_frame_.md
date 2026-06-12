---
title: "How do I capture and Process each and every frame of an image using CImg library ?"
date: 2016-05-03
forum: Education &amp; Science
---

### Post by lohith2 on 2016-05-03
Hi, I'm working on a project based on real time image processing using CImg Library in Raspberrypi.
 

 I need to capture images at higher frame rates (say atleast 30 fps), when I use the inbuilt Raspicam commands such as
 

     sudo raspistill -o -img_%d.jpg -tl 5 -t 1000  -a 512
 

 /* -tl : time lapse duration in msec
     -t  : total time duration (1000 msec = 1 sec)
     -a : displays frame numbers  
 */
 

 with this command though it shows 34 frames per second,I could only capture maximum of 4 frames/images (and rest of the frames are skipped) and by reducing the resolution and quality of the images I could capture at a maximum of 7-8 images per second.
 

 But I don't want to compromise on the quality of an image since I will be capturing an image, processing it immediately and will be deleting an image to save memory.  
 

 Later I tried using V4L2(Video for Linux) drivers to make use of the best performance of a camera, but in the internet, tutorials regarding V4l2 and cimg are quite scarce, I couldn't find one.
 

 I have been using the following commands
   
 

     # Capture a JPEG image
      v4l2-ctl --set-fmt-video=width=2592,height=1944,pixelformat=3
      v4l2-ctl --stream-mmap=3 --stream-count=1 –stream-to=somefile.jpg
      
 

 

 (source	: [http://www.geeetech.com/wiki/index.php/Raspberry_Pi_Camera_Module](http://www.geeetech.com/wiki/index.php/Raspberry_Pi_Camera_Module))
 

 but I couldn't get enough information about those parameters such as (stream-mmap & stream-count) what does it exactly, and how does these commands help me in capturing 30 frames/images per second ?
 

 **CONDITIONS:**
 

 1. Most importantly I don't want to use OPENCV, MATLAB or any other image processing softwares, since my image processing task is very simple (I.e detection of led light blink) also my objective is to have a light weight tool to perform these operations at the cost of higher performance.
 

 2.  And also my programming code should be in either C or C++ but not in python or Java (since processing speed matters !)
 

 3. Please make a note that,my aim is not to record a video but to capture as many frames as possible and to process each and individual images.  
 

 Now I have the following code in OpenCv which performs my task, but I request you to help me in implementing the same using CImg libraries (which is in C++) or any other light weight libraries or something with v4l2
 

     #include <iostream>
     #include <opencv2/opencv.hpp>
 

     using namespace std;
     using namespace cv;
 

     int main (){
 

     VideoCapture capture (0); //Since you have your device at /dev/video0
 

     /* You can edit the capture properties with "capture.set (property, value);" or in the driver with "v4l2-ctl --set-ctrl=auto_exposure=1"*/
 

     waitKey (200); //Wait 200 ms to ensure the device is open
 

     Mat frame; // create Matrix where the new frame will be stored
     if (capture.isOpened()){
     while (true){
     capture >> frame; //Put the new image in the Matrix
   
     imshow ("Image", frame); //function to show the image in the screen
 

     }
     }
     }
     }
 `
 

 * I'm a beginner to the Programming and Raspberry pi, please excuse if there are any mistakes in the above problem statements.
 

 Awaiting your favorable suggestions and any help is really appreciated.
 

 Thanks in advance
 

 Best Regards
 BLV Lohith Kumar

---

