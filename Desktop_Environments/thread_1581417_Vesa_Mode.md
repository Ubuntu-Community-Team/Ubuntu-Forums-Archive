---
title: "Vesa Mode"
date: 2010-09-24
forum: Desktop Environments
---

### Post by alms66 on 2010-09-24
I ran Lubuntu live on an old computer system to see if it would work, and using Vesa mode, it works perfectly.  The problem is, that once installed, it tries to use the video card, an old ATI card that isn't supported.  I want it to start in Vesa mode by default, how do I go about setting that up though?  Btw, I try to at least get to the command line during startup after successfully installing Lubuntu and I can't even get to that - despite it running perfectly live...
I'm lost here, please advise.
Thanks.

---

### Post by alms66 on 2010-09-26
bump
:guitar:

---

### Post by cavalier911 on 2010-09-29
At the grub menu choose recovery mode.
From the recovery menu choose command prompt.
Login then:
```
sudo X -configure
```That should generate /root/xorg.conf.new
```
sudo nano /root/xorg.conf.new
```Scroll down to Section "Device" 
Change Driver "**your.unwanted.driver**" to Driver "**vesa**"
Save 
Now rename/copy
```
sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
```Reboot

---

