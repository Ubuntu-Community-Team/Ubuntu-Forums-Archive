---
title: "Problem with nVidia drivers"
date: 2005-12-29
forum: General Help
---

### Post by justintime32 on 2005-12-29
I just did a fresh install of Ubuntu Breezy 5.10. So far so good, except for one problem.

I have a (pretty old) nVidia graphics card (a Riva TNT). I want to install the proprietary drivers so dragging windows around won't be so sluggish (I have no intrest in 3D acceleration, this machine isn't really cut out for that). I installed the nvidia-glx package, as instructed in the wiki, and ran 'sudo nvidia-glx-config enable'. It exited without printing anything, so I assumed it worked. I logged out and did a Ctrl + Alt + Backspace, but didn't see the nvidia splash screen come up. Looking in the xorg.conf file, the nv driver was still being used. I manually changed it to nvidia, but then I got an error saying that no screens were found, and 'sudo modprobe nvidia' returns this:
```
FATAL: Error inserting nvidia (/lib/modules/2.6.12-10-386/volatile/nvidia.ko): No such device
```
Hmm... I also updated the kernel on first boot, would that have anything to do with this?

---

### Post by Perfect Storm on 2005-12-29
Try with the nvidia legacy drivers. They are for older cards, but first remember to uninstall your current driver first.

---

### Post by tlc on 2005-12-29
The latest nvidia drivers don't work with old TNT/TNT2 cards.

---

### Post by lviggiano on 2005-12-29
[QUOTE=tlc]The latest nvidia drivers don't work with old TNT/TNT2 cards.[/QUOTE]

I think that the right thing, is to write to hardware manufacturer: they should know that their customers need drivers for linux. I did so for my Epson EPL 5700L printer, that currently has no way to work with Linux (I have to reboot in windows).

---

