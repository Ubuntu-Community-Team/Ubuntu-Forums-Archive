---
title: "webcam not working in 10.4"
date: 2010-05-25
forum: Desktop Environments
---

### Post by Rahul_G on 2010-05-25
hello all,

the webcam does not work with 10,4. i tried using skype and then even tried the following on the terminal window:
"rahul@rahul-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not open device "/dev/video0" for reading and writing. [v4l_calls.c(179): gst_v4l_open (): /GstPipeline: pipeline0/GstV4lSrc:v4lsrc1:
system error: No space left on device]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Could not open device '/dev/video0' for reading and writing. [v4l2_calls.c(502): gst_v4l2_open (): /GstPipeline: pipeline1/GstV4l2Src:v4l2src1:
system error: No space left on device]
"
Any idea on how to solve these errors and get the webcam working?

Thanks in advance.

---

### Post by tanmay_gaur on 2010-07-20
I am also facing the same problem. On (gstreamer-properties), I receive error "Video for Linux (v4l): Device "/dev/video0" does not exist.". I have tried all possible solutions. It seems my webcam which is being detected on lsusb, is not supported by Ubuntu 10.04.
"Bus 004 Device 003: ID 093a:2462 Pixart Imaging, Inc. " Or is a bug with my settings? Can anyone help?

---

### Post by LucianoP on 2010-09-08
I have exactly the same problem 
=(

---

### Post by 0N3 on 2010-09-08
Im not sure if this will help but a good program for web camera is webcamstudio available here

[http://www.ws4gl.org/](http://www.ws4gl.org/)

---

### Post by isaacahloe on 2010-10-20
this also effects me but when i upgraded to maverick

---

