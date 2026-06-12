---
title: "USB webcam only works when plugged in at boot"
date: 2006-03-03
forum: Desktop Environments
---

### Post by IndigoMontoya on 2006-03-03
Hi!  I am having a strange (I think) problem with my usb webcam.  It is a Intel Create and Share CS330.  It uses the spca5xx driver which I installed from piecing together a few things from this forum and a few other web forums.  I am not brand new to linux, but I am aware that there is plenty I do not know. 

I can successfully modprobe the driver with out an error so I know it is working, BUT the camera will only be seen if it is plugged in when I boot the computer.  If I have it plugged in at boot I can use gqcam and gnomemeeting and camorama just fine.  But when I plug it in after booting, nothing works ("/dev/video - no such device") I have tried making a link from /dev/video0 to /dev/video to no avail.  I have had a similar problem with a usb flash card reader I have, but when I try a friend's it worked fine (being plugged in and mounted automatically).  So to fix that problem I just dont use that reader (it is ancient so I thought IT was the problem).  When I plug in the webcam and try lsusb, I get nothing listed (well the command works, just no device is listed), where as if it is plugged in at boot I see it listed.  In a previous install of Ubuntu I tried to remove and reinstall hotplug (or hal - I forget which) and it removed a bunch of other stuff with it (and still did not work!). 

Does anyone have any suggestions or tips to how I can get this to work?  I feel like there is a bigger problem then my webcam, either HAL or Hotplugging ot something, but I have no idea how to approach it.

Thanks a lot,
Scott

---

### Post by IndigoMontoya on 2006-03-05
Any body help?

---

### Post by sham69 on 2006-03-05
I think you are pretty lucky it actually works in Linux!
Hot plugging would be nice, tho';)

---

### Post by IndigoMontoya on 2006-03-06
Yeah.  This is very true.  I am more concerned that certain things work with hotplugging and other do not (some flash card readers do, others do not).  I was just hoping someone had an idea.  

I guess once I put some time into shortening my bootup (I plan a recompiled kernel with most modules compiled into the kernel and try out InitNG too) I can just reboot when necessary for the few webcam things I do.  And the fact I have a second card reader that works is good enough.  A solution would just be icing on the cake.

---

### Post by leech on 2006-03-06
Well, it may work in Dapper.  Finally they've done away with Hotplug and now Udev handles all of that.  Though last time I tried (which was a while ago, I admit) the udev in Dapper was a little broken for Joystick support.  The udev in Debian Sid is much newer and works as well.  Dapper has version 0.79, whereas Debian Sid's is version 0.86.  Not that it really matters, since they're just a bunch of scripts, but the udev scripts even when they were the same versions were completely different than the ones for Debian.  I just know that it worked flawlessly in Debian, and in Dapper, I had to tweak stuff.

Leech

---

### Post by IndigoMontoya on 2006-03-06
Great.  So here is a potentially stupid question:  Is there a way to update to this new udev system and turn off hotplugging without totally converting to dapper?  Don't get me worng, I would love to go to Dapper, but I just don't feel safe changing my main computer to a potentially unstable environment (I am trying to write my thesis and don't need a crash at the wrong time).  Would that be possible?

Thanks!

---

### Post by IndigoMontoya on 2006-03-09
So now I did the same thing I did the first day I had it working, and I can open camorama, but the image is messed up.  I know it is seeing something, but it is only the bottom portion of the screen and very garbled and unclear.  If I hold it to my screen I can see the text, so it is semi working, but not really.  I tried removing and inserting the module again.  I even recompiled and reinserted the module.  All to no avail

---

