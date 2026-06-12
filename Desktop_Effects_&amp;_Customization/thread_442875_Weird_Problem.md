---
title: "Weird Problem"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by coolzgeek on 2007-05-13
I installed the NVIDIA-new driver and my resolution went crazy. After fixing it, the default resolution was 1280x1024 which was the desired one. When i restarted, my login screen's resolution is wrong but when i log in to either KDE or GNOME, the resolution is fine. What is going on?

---

### Post by hartz on 2007-05-14
See if this sorts it out:

sudo dpkg-reconfigure xserver-xorg

---

