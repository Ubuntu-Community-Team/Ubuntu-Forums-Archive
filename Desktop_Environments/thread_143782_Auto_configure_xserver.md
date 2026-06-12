---
title: "Auto configure xserver"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Gujs on 2006-03-13
Hello,

I would like to start auto configure of xserver. I have a new video card and xserver is still forsing config of an old one and it fails to start. 

If exists something like initial configure script plese tell me about it?

Thanks!

---

### Post by meborc on 2006-03-13
may be **sudo dpkg-reconfigure xserver-xorg** is what you are looking for?

or manually editing your **xorg.conf**

---

### Post by kaamos on 2006-03-13
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Is the script run on install.

---

