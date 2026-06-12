---
title: "Vostro 1500"
date: 2007-08-12
forum: Dell  Ubuntu Support
---

### Post by pcrusaderz on 2007-08-12
I am brand spankin new to Ubuntu in just about every form.  I did not see a direct thread about this yet, please merge or guide me to one if already exists.

Question is around the display on a Vostro 1500.  I have the Intel 965 built in chipset and I am wondering if anyone is having success getting this to work with Ubunto.  I am running 7.04

My error is it cannot find a Screen (paraphrase) out of xorg.conf.

Any help is appreciated.  Thanks!

---

### Post by davidmorawski on 2007-08-12
Check out [this]("http://ubuntuforums.org/showpost.php?p=3177135&postcount=2") post and [this]("http://ubuntuforums.org/showthread.php?t=481651") thread. 

The D630 uses the same chipset, so the hints found in the above links may help you out.

If you're still having trouble, post your /etc/X11/xorg.conf and /var/log/Xorg.0.log files, and the output from running the command `lspci`.


Dave

---

### Post by pcrusaderz on 2007-08-12
Thanks.  First link did the trick with supplimental xorg suggestions did the trick.  It looks great.

---

### Post by driztin on 2007-08-12
Also when you running the xconfig you might will probably want to select all the screen resolutions. i ran though with mine last night. the screen resolution is 1200 x 800 so make sure when it askes what resolutions you want to use select them all so that is can select the correct one for your display.

---

