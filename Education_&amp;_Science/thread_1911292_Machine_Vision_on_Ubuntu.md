---
title: "Machine Vision on Ubuntu?"
date: 2012-01-18
forum: Education &amp; Science
---

### Post by 1script on 2012-01-18
Can someone recommend an application for the subject?

I'm looking for a software that would let me recognize a shape from a video camera feed (a webcam looking down on a conveyor) and send a command via serial interface? This is for a simple educational robotic setup. I would also appreciate any tips or advice on how to get started with machine vision in Linux in general.
Thanks!

---

### Post by kaspar_silas on 2012-03-09
The easiest way into Machine Vision is a program called Harpia.
(It's in the repos)
 
This is actually a nice graphical wrapper for the powerful opencv (Open Source Computer Vision) libraries.

Anyway that should let you get started.

---

### Post by Helen McCall on 2012-03-19
> **kaspar_silas said:**
> The easiest way into Machine Vision is a program called Harpia.
(It's in the repos)
 
This is actually a nice graphical wrapper for the powerful opencv (Open Source Computer Vision) libraries.

Anyway that should let you get started.

I just installed Harpia to have a look at it. It doesn't, on first look, appear to have any functions for image recognition. I used to develop image recognition methods in the nineties, with a few good published papers on the subject. Is there any easy way of combining the power of Octave with Harpia?

---

### Post by kaspar_silas on 2012-04-12
Harpia is merely a nice GUI wrapper for openCV. It's openCV that is the massive very optimized coding library specifically for real time computer vision. Harpia is really just a nice little beginners ramp up.

I didn't realise you had background in this in that case you can probably jump straight to openCV

[URL="http://opencv.willowgarage.com/wiki/"]
http://opencv.willowgarage.com/wiki/ [/URL]

which you can of course call from within Octave:
[http://octave-swig.sourceforge.net/octave-opencv.html](http://octave-swig.sourceforge.net/octave-opencv.html)

---

### Post by George B on 2012-04-16
Also if you're interested in robotic applications I'd suggest getting to know [ROS]("http://www.ros.org/wiki/") as soon as possible, and as it's been said OpenCV is great for 2D applications, you just have to know a little, maybe a bit more ;) , programming to use it's libraries and if you ever want to move into 3D for example from a Kinect I happily recommend [PCL]("http://pointclouds.org/").

---

### Post by kaspar_silas on 2012-04-17
> **George B said:**
> .... and if you ever want to move into 3D for example from a Kinect I happily recommend [PCL]("http://pointclouds.org/").

Damn that looks really good. Next few month's play project is sorted.

---

