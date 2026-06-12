---
title: "webcam errors out"
date: 2012-11-25
forum: Desktop Environments
---

### Post by Bynw on 2012-11-25
I am running xubuntu 12.04 and every time I attempt to use any program running my webcam it errors out.



using guvcview

I get this error:

fps is set to 1/1
Checking video mode 320x240@32bpp : OK 
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable

using ffserver to create a stream I get this error:

bynw@jast:~$  ffserver -f ~/ffserver.conf & ffmpeg -v 2 -r 5 -s 640x480 -f video4linux2 -i /dev/video0 [http://localhost:8090/webcam.ffm](http://localhost:8090/webcam.ffm) 
[1] 24365
avserver version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:33 with gcc 4.6.3
Aborted (core dumped)


using webcam i get this error:

bynw@jast:~$  ffserver -f ~/ffserver.conf & ffmpeg -v 2 -r 5 -s 640x480 -f video4linux2 -i /dev/video0 [http://localhost:8090/webcam.ffm](http://localhost:8090/webcam.ffm) 
[1] 24365
avserver version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:51:33 with gcc 4.6.3
Aborted (core dumped)


I have used several of these programs before without error on previous version of *ubuntu and they have worked just fine. Any help to get them to work on xubuntu would be greatly appriciated.

Thank you.


i've included a lsusb info
bynw@jast:/media/ossus$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 059b:0370 Iomega Corp. 
Bus 002 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro
Bus 001 Device 004: ID 03f0:3e17 Hewlett-Packard LaserJet P1006

---

