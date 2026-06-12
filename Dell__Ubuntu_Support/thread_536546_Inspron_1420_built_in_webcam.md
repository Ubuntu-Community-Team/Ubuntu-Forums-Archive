---
title: "Inspron 1420 built in webcam"
date: 2007-08-27
forum: Dell  Ubuntu Support
---

### Post by RancidLM on 2007-08-27
Is there support for the webcam yet? i haven't been able to get any kernel modules to get a /dev/video
if i do a lsusb i get it listed as
Omnivision Technologies, Inc.

any one?
Thanks!

---

### Post by linuxwizard on 2007-08-27
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by daageep on 2007-08-28
follow this link:

[http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

it is for the 1520, but it has worked for my vostro 1400 (which i think should be really similar to your 1420).

basically the driver needs to know about the webcam. you add lines in the source with the webcam information and recompile the driver module.

Please tell me if you get your mic working (the ones to the sides of the webcam) though! I can't figure it out!

---

### Post by thecure on 2007-09-16
> **RancidLM said:**
> Is there support for the webcam yet? i haven't been able to get any kernel modules to get a /dev/video
if i do a lsusb i get it listed as
Omnivision Technologies, Inc.

any one?
Thanks!
 
I have Inspiron 1420 with the omnivision webcam also. Haven't figured out how to use it in any of the proper webcam programs but in Zapping TV program it works! So there has to be a way to configure it for the rest of the programs. (Running Gutsy)

---

### Post by thecure on 2007-09-17
> **thecure said:**
> I have Inspiron 1420 with the omnivision webcam also. Haven't figured out how to use it in any of the proper webcam programs but in Zapping TV program it works! So there has to be a way to configure it for the rest of the programs. (Running Gutsy)

Forgot to mention I installed the uvc driver.  In Ekiga the webcam works great. The only thing left for me is to get the mic to work.

[uvc driver instructions]("http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS") If my compiled drivers would help anyone I could send the files (Gutsy)

---

### Post by WAB on 2007-09-27
Hi guys, I have a Inspiron 1420, vista based, but now Ubuntu Feisty is working fine. 

From the thread: [http://ubuntuforums.org/showthread.php?t=501195](http://ubuntuforums.org/showthread.php?t=501195)

I took these instructions: 

 sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko && sudo depmod -ae

I don't know if the driver is working. I'm trying to use it with amsn, but when want to use it,I see

"
Type: IP-restrict-NAT 
Listening: FALSE

you are firewalled or behind a router" 

I want to know, How can I to solve this problem?

Please, I don't  want to see the same crap of the wikis like "configure your router....." or "open ports in your firewall..." I don't have any router. 

I Installed Firestarter, but that didn't solve my problem, in fact I disabled it completely. Additionally, programs which use webcam under Vista, work correctly. 

When I start amsn webcam services, the blue LED next to the cam lent turn on for a short moment. 

Please help!!

---

### Post by irwjager on 2007-10-04
> **thecure said:**
> Forgot to mention I installed the uvc driver.  In Ekiga the webcam works great. The only thing left for me is to get the mic to work.

[uvc driver instructions]("http://openfacts.berlios.de/index-en.phtml?title=HowTo_compile_for_Ubuntu_6.06_LTS") If my compiled drivers would help anyone I could send the files (Gutsy)

I'm in the same boat; all is working fine in Ekiga, except the internal mic. I tried all the guides i could find, compiling ALSA 1.0.15rc3, copiling latest kernel from kernel.org and ritually sacrificing an iPhone to teh Tux. None of it worked.

I'm really really stuck guys...

---

### Post by linuxwizard on 2007-10-04
irwjager
See if these will help on your mic

[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by ubermenschx on 2007-12-21
Nope. those links dont help for the 1420(n)....Stuck on same issue

---

### Post by jdelaros1 on 2007-12-21
See

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work)

---

### Post by dnvikram on 2007-12-22
Add the package CHEESE from the ubuntu repository...I have Ubuntu Gutsy on my Inspiron 1420..and the bwecal workfs perfectly fine and infact is awesome...

---

### Post by dnvikram on 2007-12-22
add the package cheese .I have webcam working on my gutsy on 1420N Inspiron.

---

### Post by thecure on 2007-12-23
> **dnvikram said:**
> add the package cheese .I have webcam working on my gutsy on 1420N Inspiron. 

Update: The final release version of Gutsy the webcam worked out of the box Inspiron 1420.

---

### Post by dnvikram on 2007-12-24
Download the package ,"cheese".It shud get ur webcam on 1420N up and running in wink of an eye.

---

### Post by ubermenschx on 2007-12-24
Only problem i can see is the frame rate...a little slow. Anyone know how to tweak to be a little faster?

---

