---
title: "Dell 1564 Webcam / Ubuntu 10.10"
date: 2010-09-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TBURGESS on 2010-09-30
Hi;

I have a Dell 1564 and I installed Ubuntu 10.10.  My built in webcam (Laptop_integrated_Webcam_1.3M(dev/video1)) doesn't work.

Cheese shows a black window where the image should be.
 - I tried each available resolution
Skype shows a black window when I do a Video test.
Guvcview shows a black window for the video and all the controls
 - Run from terminal shows:
   libv4l2: error dequeuing buf: Invalid argument
   VIDIOC_DQBUF - Unable to dequeue buffer : Invalid argument
   Error grabbing image

Anyone have a solution to this problem?

uname -a
Linux tburgess 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
lsusb
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 057: ID 0c45:6480 Microdia                                  <-------
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

If you need any additional information, please let me know so I can provide it.

Thanks.

---

### Post by mörgæs on 2010-10-02
Since 10.10 is not finished and stable, expect to find lots of these bugs. I would stay with 10.04 at least until Christmas.

---

### Post by jimned on 2011-04-02
I have the same problem with my Dell 1564 and it's after Christmas.  Any fix or recommendations?

---

### Post by jpirate78 on 2011-04-07
I have had the same issue with my Dell Inspiron 1545 with Integrated Web Cam.  The distro I'm using is Ubuntu 10.04.

---

### Post by dyem1 on 2011-05-19
Same here... it's a shame it doesn't work. For me, it works in certain occasions. Tested with ubuntu 10.04 and ubuntu 11.04. I tried to change settings of gstreamer-properties, video input, and in one occasion it worked...

---

### Post by kokonobs on 2011-07-02
For anyone still having issues with this.. I followed the instructions here

[http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/)

So far everything is working perfectly. I did not understand what it all does but all i know is that it works great. 

It might be necessary to repeat it when there is a kernel update (someone with more knowledge please confirm)

Thanks

UPDATE: This did not provide a lasting solution. It just remained as it was, working randomly every now and then. But alas the root of the problem has been found and its not software related. see dell support link below, post by medic29

[http://en.community.dell.com/support...px?PageIndex=1](http://en.community.dell.com/support...px?PageIndex=1)

---

### Post by dyem1 on 2011-07-12
Didn't work for me that last tip.

---

### Post by kokonobs on 2011-08-17
check update

---

### Post by GonzalitoUY on 2011-11-18
Bump? I got an Inspiron M5010R,using 11.10, and the same webcam (0c45:6480)works fine, but on Skype, it just freezes :(
The link posted to dell support site doesn't work

---

