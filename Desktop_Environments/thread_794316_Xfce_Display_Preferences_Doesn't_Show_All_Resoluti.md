---
title: "Xfce Display Preferences Doesn't Show All Resolutions"
date: 2008-05-14
forum: Desktop Environments
---

### Post by timkoop on 2008-05-14
Hopefully this should be a quick one to answer.

In Xubuntu 8.04 Xfce Settings Display Preferences, there is a list of valid screen resolutions to choose from.  My list only shows 800x600@56 and down.  But in Windows it can easily display 1024x840@75.  How do I get the real list?

I've looked around and it seems everyone says to edit xorg.conf.  But is this really the best thing to do now since xorg configures everything itself?

Part of my xorg.conf file is this:
Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Thanks a lot in advance.

I don't know what kind of graphics card I have.  If it makes a difference, just tell me how to find out and I'll post it.

Oh, and I just changed monitors recently, after I installed Xubuntu.

--
Tim Koop

---

### Post by bapoumba on 2008-05-14
if you changed monitor, you probably need to reconfigure xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by timkoop on 2008-05-15
> **bapoumba said:**
> if you changed monitor, you probably need to reconfigure xorg.conf:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Thanks.  I appreciate the reply, but alas it didn't do anything.  Any other ideas?  I even restarted X (with ctrl-alt-backspace) and the list of resolutions is still short.

Perhaps can I install some sort of screen and graphics configuration from Ubunutu or Kubuntu?  Would this work and how would I do it?

Thanks a lot!

--
Tim

---

### Post by timkoop on 2008-05-16
So, I finally got it working.

I ran this:

sudo displayconfig-gtk

This brings up the display configuration screen as seen in Ubuntu.  I played around with the monitor type, which gives me a bigger list of resolution types.  I picked something that worked.

---

### Post by bapoumba on 2008-05-17
Cool, glad to see you got it working and thanks for coming back and posting the solution. It can be helpful to others :)

---

