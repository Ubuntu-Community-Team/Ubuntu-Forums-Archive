---
title: "more webcam troubles (1420)"
date: 2008-05-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sanjuuichisandoichi on 2008-05-21
Ok, I'm very new to ubuntu, but am enthusiastic so bear with me.

I just bought an inspiron 1420 prepackaged with ubuntu, now I wanted to make it dual boot xp as well as ubuntu and in the process I think I messed things up, so I tried a clean re-installation of ubuntu (and will use wine for all windows needs).

Most things seem fine but I am having trouble with the webcam still

lsusb tells me
```
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 1241:1166 Belkin 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 
```
which looks like it sees the webcam

trying to open camorama tells me "could not connect to video device (/dev/video0) Please check connection.  This also makes the little blue light next to my webcam blink.

I figure I might just need a driver, which dell seems to think they have provided on a disc, but it is an executable which I can't seem to make run.

Any help would be fantastic!

---

### Post by notwen on 2008-05-21
Which version of Ubuntu did you install on it?

---

### Post by sanjuuichisandoichi on 2008-05-21
oops, it was originally 7.10 and i reinstalled 7.10

---

### Post by notwen on 2008-05-21
Try [this]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work").  Post back and let me know the results.  =]

---

### Post by sanjuuichisandoichi on 2008-05-21
Aha! it's working with Ekiga now. Thank you!

I still get the same error from camorama, but I might just search for a different app.  Is there anything comparable to a mac's photobooth?

---

### Post by notwen on 2008-05-21
Sorry, I don't have a cam on my Inspiron 1420n, so I have little experience w/ webcam related apps. Glad you were able to get it up & running.  Best of luck to you.  =]

---

### Post by svega85 on 2008-06-06
you may want to try cheese

---

### Post by starcannon on 2008-08-13
My 1420n the camera works for anywhere from 10seconds to 10 minutes then freezes. I have the same issue on my HP dv2600.

Only option to fix it is to use the restore dvd that I burned before I did my own install. /sigh.

If anyone knows of a guide, or the work around, I'd be very interested.

Programs I've tried:
Cheese
Skype
Ekiga
Canorama
VLC
aMSN i think it was, which ever IM supports webcams(its been awhile)

---

### Post by svega85 on 2008-08-14
I have this same bug my cam only works 10seconds or less  here [https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/246089](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/246089) is the bug report. you may be able to help us test some stuff so we can figure it out.

---

