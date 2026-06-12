---
title: "Screen resolution problem"
date: 2008-03-29
forum: Desktop Environments
---

### Post by Naijakid on 2008-03-29
Help!  

I'm a new user.  I've installed Kubuntu as a dual boot with Windows XP on an older  laptop  Dell Inspiron 2500.  Installation seems successful.  But resolution is stuck at 640x480.  (Reminds me of my first computer, an IBM PC Jr.!)

Meanwhile, the XP on its partition side" works fine and looks good with res. set at 1024x768.

I have gone thru the sudo dpkg-reconfigure xserver-xorg sequence and have set resolution modes to 1024x768, 800x600, and 640x480 (the three that are listed as possibilities by Windows XP).  Still seems to recognize only 640x480.  

I changed the "device" to Intel 82815 which the computer has -- still doesn't work.

This portable has a celeron processor.

Any help much appreciated!

---

### Post by chucky chuckaluck on 2008-03-31
does 1024x768 appear in the 'screen' section of your /etc/X11/xorg.conf file? if it doesn't you can add it directly to the file (preceding the other possible resolutions, and you'd have to do it with root priviledges). once it's there, you should be able to go into kcontrol>kde components>display (i think it is) and select the desired resolution.

---

### Post by boltorg on 2008-05-30
Fix for 1024x768

_[Thread]("http://ubuntuforums.org/showthread.php?t=750372")_

---

