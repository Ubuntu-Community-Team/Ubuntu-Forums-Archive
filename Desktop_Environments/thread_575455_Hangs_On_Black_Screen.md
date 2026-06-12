---
title: "Hangs On Black Screen"
date: 2007-10-14
forum: Desktop Environments
---

### Post by Dak1n on 2007-10-14
Hi, I have been running Ubuntu for a few weeks now, now whenever I start up my computer I will see the Ubuntu loading bar but then it doesn't show the login screen, just a black screen with no cursor. I can start it up in text only mode by pressing escape just before the Ubuntu loading bar shows, then selecting the Recovery Mode.
Thanks.

---

### Post by mindtrick on 2007-10-14
When you're in text mode 

> sudo dpkg-reconfigure -phigh xserver-xorg 

Choose the correct settings for your system. Usually it happens when your graphics driver settings get messed up.

---

### Post by Dak1n on 2007-10-14
Hi, I get the error message that xserver-xpog isn't installed.

---

