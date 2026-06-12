---
title: "Closing lid -&gt; Locked desktop -&gt; video playing is broken for that session"
date: 2005-04-19
forum: Desktop Environments
---

### Post by Abasher on 2005-04-19
Hi!

I seem to have a wee problem. When I close the lid to my laptop it does something. When I open it again the desktop is locked, and I have to type in my password again. 

First of all, this is really irritating - I don't want anything to happen. I just want it to be like as if I pushed the power button on the monitor on my stationary system. I am, however, unsuccessful to find anywhere to turn this 'feature' of.

Second, this causes problems. After I opened the lid I am unable to play video files. When opening any kind of video media (MPEG, MPEG4 in avi container) the image where the video should be is just blue. Seems like overlay never quite recovered from the wierdo things the Ubuntu does when I close my lid.  ](*,) 

If it helps, my system is a Fujitsu-Siemens Lifebook C1020. With a S3 ProSavage graphics adapter. Kernel version: 2.6.10-5-686.

---

### Post by laka on 2005-04-19
First of all, i think that feature is really nice :) 

Run xscreensaver-demo and turn off the screen saver. If that doesn't help, try to see under advanced.

---

### Post by Abasher on 2005-04-20
Hello, and thanks for the quick reply!

I'm afraid, however, that that didn't quite solve my problem.

I've had the screensaver turned of since I started using Ubuntu. The advanced tab has no options for customizing the behavior when operating the lid. Tried unchecking Power management, but the same problem occurs.

Anyone knows why this feature borks my video-playing capabilities?

---

### Post by Roptaty on 2005-04-20
Hello, I had the same problem. I renamed lid.sh which you will find in /etc/acpi directory to something else... problem solved...  ugly fix but... hey.. it works. :D

---

