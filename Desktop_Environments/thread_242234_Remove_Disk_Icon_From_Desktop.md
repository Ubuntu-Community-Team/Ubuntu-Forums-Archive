---
title: "Remove Disk Icon From Desktop"
date: 2006-08-23
forum: Desktop Environments
---

### Post by loafman on 2006-08-23
I have a full tower, so I installed a 250GB drive on a USB port, reformatted to ext3 so it would not automount, turned off all automount options in preferences, and so on.  It still brings up that pesky icon on the desktop.  I cannot get rid of it.  I don't like icons on the desktop, so this is an eyesore.

Short of removing the drive, how do I remove the icon and keep it from coming back?

Thanks.

---

### Post by jkwarras on 2006-08-23
You can disable it via gconf. I don't remember where's exactly located.

---

### Post by loafman on 2006-08-23
> **jkwarras said:**
> You can disable it via gconf. I don't remember where's exactly located.
Answering my own question:
Menu: 
[INDENT]Applications/System Tools/Configuration Editor[/INDENT]
In Configuration Editor:
[INDENT]Apps/Nautilus/Desktop, 
clear "volumes_visible" checkbox[/INDENT]

---

### Post by LinLenLap on 2006-11-25
Thanks! I was trying to get rid of my xp partition from always showing up. App >Nautilus >Desktop  did the trick!

L.

*UPDATE*

Using edgy eft, and an older Ipod Shuffle, and Amarok from the repos, Ipod is no longer easily discovered and automatically mounted. I suppose Amarok is looking on the desktop, or perhaps using some shared file that nautilus uses. In any event, since the only reason I wanted to do this was to get my XP partition off the desktop, I think I'll just remove it from my fstab.

Still, the tip was useful for putting a trash icon on my desktop!

L

---

