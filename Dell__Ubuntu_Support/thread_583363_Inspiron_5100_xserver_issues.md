---
title: "Inspiron 5100 xserver issues"
date: 2007-10-20
forum: Dell  Ubuntu Support
---

### Post by warrior14c on 2007-10-20
I have an Inspiron 5100 with ATI Radeon Mobility 7500 (M7).  For some reason, x fails to start.  I can see the ubuntu load screen but the login screen turns black.  If I switch to the command line and do a

sudo nano /etc/x11/xorg.conf

xorg.conf is empty.  Also, booting into safe graphics mode from the live  cd does work, but if i open xorg.conf it is still empty.  What could be the issue here? If I do a lspci it does recognize the graphics card, but the gui is not working.  The interface worked just fine in Feisty.  Any ideas?  Any help would be much appreciated :)

-I'm still a linux newbie so try to be as simple as possible :(

---

### Post by Phoenix on 2007-10-20
You might be looking for /etc/X11/xorg.conf
/etc/x11/xorg.conf and /etc/X11/xorg.conf are treated as two separate things by *NIX. (Linux, BSD etc). Try doing
sudo nano /etc/X11/xorg.conf and tell us if that gets you something

--
Cheers

---

### Post by warrior14c on 2007-10-22
Issue solved!  I did exactly as you said and  used /etc/X11/xorg.conf and was able to read the file.  Then under Devices for my display adapter, I added the line

Option "LVDSBiosNativeMode" "FALSE"

It was taken from this post [http://ubuntuforums.org/showthread.php?p=3577793](http://ubuntuforums.org/showthread.php?p=3577793)

Everything works great, including the new desktop effects.  Thanks so much!

-Chris

---

