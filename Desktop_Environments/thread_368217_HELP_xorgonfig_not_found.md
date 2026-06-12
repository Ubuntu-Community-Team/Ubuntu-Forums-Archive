---
title: "HELP xorgonfig not found?"
date: 2007-02-23
forum: Desktop Environments
---

### Post by sully311 on 2007-02-23
hello all,
I, have a problem. While surfing the web i, came across a site describing Beryl... seemed cool enough follwed the instructions to the letter. All seemed well, clicked the icon on desktop, beryl seemed to be running, but no effects?

Decided to reboot. This is where the real problem started. Error message:


EE No device found

atal server error:
no screen found
X10 fatal IO error 104

From what I've gathed from the web and help boards is that I, need to through the xorgconfig process. 

All atempts have failed. Have I, broke it beyond repair? Any help would be great. I, really dont want to reinstall, restore, upgrade, customize all over again. everything was running smooth printer, dvd, mp3, flash etc. etc.

---

### Post by sully311 on 2007-02-23
I, found a solution! 

Boot Log into text only,  at promt:

 'sudo nano /etc/X11/xorg.conf

alter the file, in my case changing the monitor model number from CM2107 to "default"

reboot into text mode at promt:

'sudo dpkg-reconfigure -phigh xserver-xorg'

confirm rewritten by new back up file name

worked fro me!:popcorn:

---

