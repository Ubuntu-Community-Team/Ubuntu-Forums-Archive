---
title: "Webcast/video cast"
date: 2009-02-21
forum: General Help
---

### Post by gpearston on 2009-02-21
I am trying to find an application for Ubuntu (8.04) that will allow me to use a web camera to monitor a room.  We raise tortoises and want to be able to check on them remotely (same network though).  I thought that would be a webcast but I can not seem to find much information about such applications and what I do find is not inline with what I want.  I am hoping for:

Low frames per second (sub 1 even - 1 frame every 2-5 seconds)
Ability to auto save the video files for later review
Multiple cameras would be nice but not needed at this point
Ability to review the videos remotely via a browser or remote control application.  
Auto deletion of files after x amount of days

It seems to me that a home security package would be perfect but I can not find anything for Linux.  Normally, I have great luck trying to find the apps I want but this one is stumping me.

Any ideas, suggestions or pointers are appreciated.

Thanks!

---

### Post by klaush on 2009-03-12
I once tried "motion" which is available in the universe repository.
It can handle multiple webcams, in fact any camera which is supported by V4L drivers, and you can define which area(s) of the camera field of view are "hot" = cause the program to capture screenshots/video.

On commandline you may install it with 
```
sudo apt-get install motion
```

But first you may decide to browse possible other candidates, to get a rough list, use  
```
sudo apt-cache search webcam
```

In this list there is e.g. camgrab, camstream, ...

Regards,
Klaus

---

