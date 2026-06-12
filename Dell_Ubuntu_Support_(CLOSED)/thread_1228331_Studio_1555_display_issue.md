---
title: "Studio 1555 display issue"
date: 2009-07-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by edwardLS on 2009-07-31
Running Ubuntu 9.04 i386 Desktop installed on a Dell Studio 1555 Laptop.  I am having several issues with the display which are mostly, but not all, related to consistency.  I have tried many of the fixes found in this forum.  All seem to fix a problem but then a power down and restart cycle seems to raise inconsistent performance.  (1) Frequently the resolution is incorrect, (2) frequently the resolution is correct, but the screen has a 4-5 inch dark strip on the right side of the screen, (3) the brightness control very inconsistent - sometimes it works, and sometimes it don't, (4) sometimes the mouse pointer is jittery, and applications seem to hang, (5) the text sometimes is not sharp or clear.

The Studio 1555 has the Intel GMA 4500.  A check in Synaptic Manager shows that the "xserver-xorg-video-intel" version install (and latest) is 2:2.6.3-0ubuntu9.3.  All Ubuntu updates have been downloaded and installed.

Is this the best display driver for the Studio 1555 with the GMA 4500 adapter?  If not, where/how do I get the best?

---

### Post by fazillatheef on 2009-08-05
I have a DELL studio 1555 but it comes with ATI 4570 .I first tried the inbuilt restricted hardware and it was stuck at 0%. So I installed the drivers using envy. It worked but the system hangs when I try to play a movie. I tried playing  the video that came with ubuntu(ogv). Compiz works really well except the video problem. I checked the forum and found that I need to turn off effects(compiz) to play videos. 

I have brightness issue and its weird too. The brightness control works only for a few minutes after the system boots. The sound was not working until I did the following:-
sudo gedit /etc/modprobe.d/alsa-base.conf
Then add this line to the file-
options snd-hda-intel model=dell-m6
 
For the time being I am using Vista that came default with the laptop. Maybe by next version of ubuntu these issues would be fixed. And then I will be using ubuntu again. Because sometimes incomplete software can damage the hardware.

---

### Post by bobmendon on 2009-08-05
Did these problems exist with previous releases of Ubuntu? I have a Studio 17 with the ATI adapter and have not experienced any problems.

---

### Post by edwardLS on 2009-08-05
With the Brightness control I experience the similar issue of having it work, and then several minutes after bootup, it would not longer work.  I have come to a solution, while not perfect, is acceptable for me.  I am setting the "default" brightness for both AC and Battery operation to 50%.  Now Ubuntu boots up in the Brightness that I desire, and I don't care if the control works or not.  

I have made some minor progress, by accident, with the Screen Resolution on the Intel GMA 4500 MHD adapter.  With my accidental fixes, I have the screen resolution booting up correctly about 95% of the time.  When it does not bootup in the correct resolution, I can now manually set it correctly.  Previously, I was unable to set it manually about half the time when it was incorrect.

I am continuing to use Ubuntu 9.04 of the Studio 1555.  I need to be [Windows & Gates]-Free by April of 2010.  I have already made the transition on my Desktop.  I still have much to learn!

---

