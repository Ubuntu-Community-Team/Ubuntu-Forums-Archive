---
title: "Touchpad tap too sensitive"
date: 2006-01-19
forum: General Help
---

### Post by CubanCorona on 2006-01-19
I have a Sony Vaio PCG-641R laptop running Breezy.

The touchpad TAP is muuuuch too sensitive.  I have two questions:

Is there an easy way to change this tap sensitivity?  I don't see it in System->Preferences->Mouse

Also, I understand that drivers in Linux are loadable kernel modules, but how can I tell which module corresponds to which device (e.g. if i want to see what driver is being used for my touchpad)?  Also, what prevents two drivers for the same device from being loaded simultaneously?

I'm pretty knowledgeable about computers in general, but I'm still trying to understand the specifics of Linux.

Thanks for the help.

---

### Post by CubanCorona on 2006-01-19
bump

---

### Post by nik on 2006-01-20
Well, what kind of touchpad? If it is a synaptics, you need to make sure it is installed correctly (the synaptics driver, search the forums), then you get lots of options to set in /etc/X11/xorg.conf ...

---

