---
title: "Help With Compiz"
date: 2010-10-29
forum: Desktop Environments
---

### Post by TheZorch on 2010-10-29
Hi, I've installed Xubuntu 10.10 on my old PC and I'd like to get Compiz working.  I have a vision problem and I've found its desktop zoom and color inversion plugins to be rather helpful.

I am using Xubuntu.  My computer is a custom build PC with a 1.2GHz AMD Athlon XP, 1GB of PC2700 RAM, 8x AGP Nvidia Geforce FX 5600 card w/256MB DDR-RAM, IDE 160GB hard drive, Sound Blaster Live 5.1, and 16x DVD-RW.

Has anyone gotten Compiz to work with XFCE and how can I get this to work?  I'm very new to this so please help.

---

### Post by gordintoronto on 2010-10-29
You might give Lubuntu a try.

---

### Post by hhh on 2010-10-29
I've never used Xubuntu, but I do have an aptosid setup using Xfce and Compiz on another partition and I've installed Compiz on other Xfce partitions I've had on my computer.

You should be able to get it going, though the Nvidia 5 series uses a legacy driver. That's the main thing, has Xubuntu prompted you to install the proprietary driver, and did it install successfully? If so, procede by installing Compiz by running the following in a terminal...```
sudo apt-get update && sudo apt-get install compiz compizconfig-settings-manager compiz-fusion-plugins-main compiz-gnome compiz-gtk
```
You may need to modify your xorg.conf file, see this...
[http://wiki.debian.org/Compiz](http://wiki.debian.org/Compiz)

Then start Compiz by opening the Run dialog (Alt+F2) and running this...```
compiz --replace
```

If all is well then add compiz --replace to your startup applications.

Post back with questions and/or if you have success. Hope that helps.

---

