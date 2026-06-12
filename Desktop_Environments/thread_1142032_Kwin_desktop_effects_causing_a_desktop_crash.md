---
title: "Kwin desktop effects causing a desktop crash?"
date: 2009-04-28
forum: Desktop Environments
---

### Post by lourp on 2009-04-28
Just upgraded to kubuntu 9.04 after long time ubuntu use.

This time went the whole hog, moved to 64bit + ext4 file system.

I have an nVidia GeForce 8600 GT graphics card, and install the proprietary drivers version 180.

Everything is fine at this point, the desktop is stunningly attractive (relative to gnome anyways).

I enable desktop effects, and all the bells and whistles that I used to enjoy with compiz are there (ok perhaps not as comprehensive as compiz but impressive nonetheless).

At this point, if I walk away from the PC for an extended period, leaving myself logged in - when I return I find the login splash screen! I log back in check the uptime - it did not reboot. Run htop, I see that all RAM and swap are exhausted, and the machine is grinding to a halt. Reboot. Repeatable.

Tried many combinations (different driver versions etc), but narrowed it down to having desktop effects enabled causes this to happen. If they are disabled, I can leave the machine (logged in) overnight and return to continue as normal.

Has anyone seen this? Is Kwin crashing? Or kdm? Not sure if its because there may be a problem with KDE on ext4?

---

### Post by lourp on 2009-04-28
The only thing I haven't tried is switching over to compiz.

Is there a "clean" way to do this in KDE? ie Ubuntu endorsed. Or is hack up of rc.local to launch compiz?

Can I still get KDE look'n'feel?

---

