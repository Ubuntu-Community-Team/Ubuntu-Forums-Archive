---
title: "Upgrade from 10.04 to 10.10 caused it to be stuck at bootscreen"
date: 2010-08-23
forum: Desktop Environments
---

### Post by djsaders on 2010-08-23
Im not to sure where to post this, but i upgraded from Ubuntu 10.04 to Ubuntu 10.l0 and it gets stuck at the bootscreen, i followed the instructions on how to do a upgrade.

Im not to sure whats caused it or how to solve it, and i dont really want to reinstall 10.04 as i forgot to backup my files :oops:

So any help would be greatly appreciated

---

### Post by amauk on 2010-08-23
10.10 (Maverick) is still in Alpha

If you're not comfortable with dealing with little issues like this, then don't run pre-release versions

Any messages your machine posts would be helpful

---

### Post by djsaders on 2010-08-23
im totally comfortable running pre-release i ran 10.04 and submitted a bug, i like to help with pre-releases.

also there are no messages it just loads the purple boot screen the 5 dots change then it stops that is it.

---

### Post by amauk on 2010-08-23
take the "quiet splash" options out of the boot options
this will disable the splash screen and make the console messages more verbose
hopefully any issues will become apparent then

---

### Post by djsaders on 2010-08-23
how do i go about doing that?

---

### Post by amauk on 2010-08-23
Reboot, and after the BIOS POST, press & hold the shift key
this will bring up the grub menu

Select and edit the relevant menu entry
Remove "quiet" and "splash" options from kernel line

Ctrl-X to boot with the altered boot line

---

