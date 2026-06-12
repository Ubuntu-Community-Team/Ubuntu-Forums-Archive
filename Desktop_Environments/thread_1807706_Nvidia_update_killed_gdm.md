---
title: "Nvidia update killed gdm"
date: 2011-07-19
forum: Desktop Environments
---

### Post by LordOrange on 2011-07-19
I recently updated my Nvidia driver and since don't have a gui. When my pc loads it just gives me a list of the start up commands. any ideas?

---

### Post by wildmanne39 on 2011-07-20
> **LordOrange said:**
> I recently updated my Nvidia driver and since don't have a gui. When my pc loads it just gives me a list of the start up commands. any ideas?Hi, if you are using 11.04 you can use these two commands and it should get you into the desktop.
```
sudo rm /etc/X11/xorg.conf
```
```
sudo dpkg-reconfigure xserver-xorg
```
Just hold the shift key down and choose root recovery with network then enter the commands.

---

### Post by LordOrange on 2011-07-20
said it can't remove it because there's no such file or directory. Tried the second line anyway but it doesn't seem to have changed anything

---

### Post by wildmanne39 on 2011-07-20
> **LordOrange said:**
> said it can't remove it because there's no such file or directory. Tried the second line anyway but it doesn't seem to have changed anythingHi, try the options at this link and it should get you in then you can work on your driver issue.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

