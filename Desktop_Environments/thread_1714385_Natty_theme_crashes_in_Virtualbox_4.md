---
title: "Natty theme crashes in Virtualbox 4"
date: 2011-03-25
forum: Desktop Environments
---

### Post by lee_connell on 2011-03-25
Anyone having problems with the theme crashing using natty in virtualbox 4?

I log in and you see the default ubuntu theme, then about 5 seconds it switches to an older gnome light theme and can't be switched back. Every once in a while, possibly due to updates or something it stays on the correct theme, but as soon as I restart the vm, it starts happening again.

Any reason for this?

---

### Post by shaoxuan on 2011-04-02
> **lee_connell said:**
> Anyone having problems with the theme crashing using natty in virtualbox 4?

I log in and you see the default ubuntu theme, then about 5 seconds it switches to an older gnome light theme and can't be switched back. Every once in a while, possibly due to updates or something it stays on the correct theme, but as soon as I restart the vm, it starts happening again.

Any reason for this?

Same problem here with Natty beta1 and virtualbox 4.0.4, host is Windows 7.

VMware Player does not have this problem, Natty beta1 is stable on it. But it seems Unity is not available when using VMware.

Maybe we should wait the final version of Natty release.

---

### Post by 3Miro on 2011-04-02
Ubuntu 11.04 starts using graphics card more heavily. As a result, you can only run Unity and the effects if you have graphical hardware acceleration enabled. Most VM software is not doing very well on those yet.

Basically, if you want to run 11.04 in Virtual Box, you have to use Classic Gnome - No Effects mode (which disables Unity).

---

### Post by trowe on 2011-04-07
> Basically, if you want to run 11.04 in Virtual Box, you have to use Classic Gnome - No Effects mode (which disables Unity).     That's true for VMware but not VirtualBox.  I have Unity running fine in VirtualBox but suffer the same problem of the theme changing after about 5 seconds (it happens in VMware workstation too when running Unity2d).

I read in one of the bug reports of a workaround that I've been using:

killall -9 gnome-settings-daemon && gnome-settings-daemon

---

