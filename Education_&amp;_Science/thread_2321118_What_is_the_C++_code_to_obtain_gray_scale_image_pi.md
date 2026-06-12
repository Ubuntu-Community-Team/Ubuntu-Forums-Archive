---
title: "What is the C++ code to obtain gray scale image pixel intensity values using CImg ?"
date: 2016-04-20
forum: Education &amp; Science
---

### Post by lohith2 on 2016-04-20
Hi, everyone I’m a beginner to C++ and raspberrypi, Here I’m working on a project to capture the real time images using Raspberrypi CSI camera and to perform simple image processing operation in C++ using CImg library.

That is, to detect the bright spot in an image (such as LED light glow) and if detects the bright spot, output should be given as ‘1’ and if not (when the LED is off ) output should be given as ‘0’.

Note: The image processing has to be done only in the specific portion of an image (i.e focus only on the led section of an image and neglecting remaining portion of an image which is out of interest, such that it saves processing time and improves performance)

But firstly I don’t know how to get pixel intensity values of a **gray scale image** using CImg library such that we can compare the values obtained in the pixel to the threshold value and problem could be solved ( this is my algorithm for the above operation but any other simpler methods for the above processing ,your suggestions are always welcome )

Could you help me in a C++ code or algorithm to perform the above task.
Thanks in advance.

---

