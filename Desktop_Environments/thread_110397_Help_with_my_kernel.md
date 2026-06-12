---
title: "Help with my kernel"
date: 2005-12-30
forum: Desktop Environments
---

### Post by GQed76 on 2005-12-30
I have updated my nvida drivers from their website, and all was well

Then foolishly i was following a walk through for somthing else and typed 

sudo apt-get install linux-headers-`uname -r` linux-restricted-modules-`uname -r` build-essential gcc-3.4

now i cant boot into graphical mode and im stuck in terminal

i think i just need to edit my Xorg.conf file but i dont know how to do that..im a newbie  HEEELP

---

### Post by fordfan753 on 2005-12-30
sudo nano /etc/X11/xorg.conf

---

### Post by GQed76 on 2005-12-30
Thanks..

I edied the video driver to say vesa

then rebooted, got into package manager and removed the restricted kernel.

replaced vesa with nvida and rebooted.

most likely the round about way , but it worked...now if i could just get that webcam to work

---

### Post by fordfan753 on 2005-12-30
That's actually the best way to do it without using too much command line.

Good luck with the webcam, I've never actually tried anything like that before

---

