---
title: "Logout and Switch User fails and system appears to freeze"
date: 2009-12-31
forum: Desktop Environments
---

### Post by abhi.b on 2009-12-31
Hi,

When I try to logout or switch user, the screen goes blank and does not return to the user list. This seems to cause the system to hang - I cannot even login in text mode (Ctrl-Alt-F1). Same behavior with switch user.

I am using Ubuntu 9.10, with default Gnome installation. I am running it on a Compaq Presario 6000 desktop - Pentium 4 with 256Mb RAM.

After attempting to logout, my only option is to reboot the system. The xsession-errors file indicates fatal IO errors towards the end, which seems to be at the time of logging out in the last session. Has anybody seen this issue? (xsession file attached)

Thanks,
-- Abhijit

---

### Post by abhi.b on 2010-01-01
I have found a fix. In /etc/X11/xorg.conf, I changed the driver to "intel" (was "vesa"). Everything works fine now.

It looks like vesa driver did not work well for the Intel 82845G graphics chipset on my PC.

---

### Post by mashedbear on 2010-01-17
I am having what I think is a similar problem. 

When a user logs out of the system, the system will go to a blank screen with flashing cursor, and not back to the list of available users. 

This has only stated to happen recently but I don't have an accurate date of when and what the last change might have been. 

I am running Ubuntu 9.10 64bit 2.6.31-16-generic & GNOME 2.28.1

Not sure how or where to start on tracking down the problem. 

I did recently have a problem with GRUB (legacy) and need to repair this using a live cd. Could this be related?

Thanks for any help

---

### Post by finneyabraham on 2010-02-14
> **abhi.b said:**
> I have found a fix. In /etc/X11/xorg.conf, I changed the driver to "intel" (was "vesa"). Everything works fine now.

It looks like vesa driver did not work well for the Intel 82845G graphics chipset on my PC.

Did this fix work for the first post-er? Do you have any fixes for this same problem for a system running AMD chipset? I have a work around by using a KDE logon screen.I would like to use a Gnome logon screen.

---

### Post by kleinebre on 2010-09-07
> **abhi.b said:**
> I have found a fix. In /etc/X11/xorg.conf, I changed the driver to "intel" (was "vesa"). Everything works fine now.

It looks like vesa driver did not work well for the Intel 82845G graphics chipset on my PC.

My system seemed to freeze on user switch here as well, but was still accessible through the network so it looked like a video card problem.
I definitely was running the right driver for my video card- ATI radeon
1200 series and "radeon" driver, but it seems it didn't like the 
Option Accelmethod "XAA" in my xorg.conf file. After deleting the line specifying that method, user swap once again seems to work fine.

---

### Post by mashedbear on 2010-11-13
I still get this problem intermittently. I have an nvidia card. 

In /etc/X11/xorg.conf it looks correct
```
Section "Device"
        Identifier     "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
```

Any ideas?

---

