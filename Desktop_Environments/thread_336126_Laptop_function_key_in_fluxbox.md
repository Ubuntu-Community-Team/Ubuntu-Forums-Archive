---
title: "Laptop function key in fluxbox"
date: 2007-01-11
forum: Desktop Environments
---

### Post by Zeso on 2007-01-11
Problem: laptop function key for volume does not work in fluxbox WM
Hardware: Acer 5024 (AMD 64)
OS: Kubuntu 6.10 Edgy

Note: All function keys work correctly in KDE.
Note: Brightness function key work correctly in fluxbox but not volume function key

How to set up volume function key ?

---

### Post by teejay17 on 2007-01-27
> **Zeso said:**
> Problem: laptop function key for volume does not work in fluxbox WM
Hardware: Acer 5024 (AMD 64)
OS: Kubuntu 6.10 Edgy

Note: All function keys work correctly in KDE.
Note: Brightness function key work correctly in fluxbox but not volume function key

How to set up volume function key ?
Yes, I'm curious about this as well. If anyone knows, that would be great.

---

### Post by ecovillain on 2007-04-22
i am having the same issue as well. i just installed fluxbox, and as the original poster said, my function keys work fine in KDE. it seems that the only function keys that dont work while using fluxbox are the volume up and volume down ones. 

any ideas?

---

### Post by RedSquirrel on 2007-04-23
Put something like this in your ~/.fluxbox/keys file:

```

XF86AudioLowerVolume    :ExecCommand        amixer -q set PCM 2- unmute
XF86AudioRaiseVolume    :ExecCommand        amixer -q set PCM 2+ unmute

```If that doesn't work, you'll need to do a bit more tinkering (creating an .Xmodmap file to help set things up), but try the above lines first.

---

