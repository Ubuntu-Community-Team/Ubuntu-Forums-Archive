---
title: "volume control in xbuntu"
date: 2011-05-04
forum: Desktop Environments
---

### Post by donarntz on 2011-05-04
For my new install of xbuntu (first time ever using XFCE), I'm stuck on only two things. 

1) Volume control.  I have pulse audio installed (because of the ubuntu studio apps), and previously in gnome I assigned the volume keys to f1, f2 & f3.  How can I do that in XFCE so that the nifty volume indicator pops up and shows me the level.  Can I do that?

2) Is there any way to assign a image to the users at the login screen with XFCE.  

I'm sold on XFCE, but the volume control problem in particular bug me because my pc is also my media center.

Thanks for the help,

Don

---

### Post by hhh on 2011-05-04
For the second issue, under Settings>>Login Window>>Users you'll see default face and global face directory.

For the first issue, you need to install xfce4-volumed to get the notification daemon to recognize your keyboard shortcuts. You can set the shortcuts under Settings>>Keyboard>Application shortcuts. I don't use pulse though and have no idea what the commands would be or if there even are any (here are instructions for alsa and oss... [https://wiki.archlinux.org/index.php/Xfce#Change_volume_with_keyboard_volume_buttons](https://wiki.archlinux.org/index.php/Xfce#Change_volume_with_keyboard_volume_buttons) ) .

I'm on Debian squeeze and Xubuntu's menu structure may be different so search around, or you can launch those  settings managers directly from there .desktop files which should be in /usr/share/applications.

HTH

---

### Post by donarntz on 2011-05-04
The problem I discovered (late last night, and I'm at work now so no time to fool with it) is that xfce4-volumed and pulse don't seem to play nice together.  I ended up with two volume control applets, and the pulse applet was not recognizing the adjustments.  Is there a way to run xfce4-volumed in the background without it being show on the panel?

---

### Post by hhh on 2011-05-05
xfce4-volumed is not an applet, it's a daemon and it does run in the background. That's something else in your panel...
[http://packages.ubuntu.com/natty/xfce4-volumed](http://packages.ubuntu.com/natty/xfce4-volumed)

---

### Post by donarntz on 2011-05-05
I'm having some issues with "libnotify-bin".  When that is installed, I get the nice volume up and down graphic, but it doesn't actually raise or lower the alsa slider.  When I remove it, alsa works but no graphic...

---

