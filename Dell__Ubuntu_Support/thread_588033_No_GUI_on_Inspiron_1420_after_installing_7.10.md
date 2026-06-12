---
title: "No GUI on Inspiron 1420 after installing 7.10"
date: 2007-10-23
forum: Dell  Ubuntu Support
---

### Post by frbe0101 on 2007-10-23
After installing a the latest version of ubuntu over my existing working version (7.04) I can't get the GUI to work! I tried both the gnome and kdm desktops both won't work (kdm says it running but I till have a BW command prompt). How do I fix this, or how do I revert back to 7.04 (it comes with it on disk)?

---

### Post by oddabe19 on 2007-10-23
I am having the exact same problem [http://ubuntuforums.org/showthread.php?t=587312](http://ubuntuforums.org/showthread.php?t=587312) :(

---

### Post by notwen on 2007-10-23
Did you guys do a simply upgrade through Update Manager or did you use the install disc and very possibly wipe all of your partitions(Dell's recovery partitions included)?  I myself also have a 1420n and am going to plan on waiting for a remastered image should they choose to release one.

---

### Post by oddabe19 on 2007-10-23
I fixed it.  What happened was they changed the module from i810 to intel.

here's how you fix it:

```
sudo apt-get update && sudo apt-get install nano
sudo nano -w /etc/X11/xorg.conf

look for i810 under Device, then change it so it looks like this:

Section "Device"
        Identifier      "Generic Video Card"
       Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

then hit ctrl+x, it'll prompt to save, save it, then restart.

```

---

### Post by frbe0101 on 2007-10-24
Yep that fix it! thanks.everthing works, sound, network, etc.

---

### Post by freeflyer57 on 2008-05-26
thank you so much. worked perfectly!

---

