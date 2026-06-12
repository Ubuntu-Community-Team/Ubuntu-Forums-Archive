---
title: "Automount is now acting funky after apt-get upgrade"
date: 2005-10-12
forum: Desktop Environments
---

### Post by aysiu on 2005-10-12
Recently (just yesterday) I did a ```
sudo apt-get upgrade
``` and everything seemed to go well, but now when I plug in USB devices, I get [this error](http://img436.imageshack.us/my.php?image=snapshot174tn.png). It doesn't appear as an icon on the desktop, as it used to, and I checked the system settings to make sure mounted devices *should* appear on the desktop. It does, however, mount. When I go to the /media folder, [the device is there](http://img442.imageshack.us/img442/614/snapshot183gc.png). There's no way for me to [graphically unmount it](http://img442.imageshack.us/img442/9712/snapshot190li.png), though.

I even tried logging in as another user--same problem.

Has anyone else experienced this problem lately?

P.S. Everything was working just fine until yesterday. I would plug in a device. It would mount and appear on the desktop. When I right-clicked the desktop icon, I could graphically unmount it, and the icon would disappear afterwards.

---

### Post by Takis on 2005-10-12
You running Breezy or Hoary?

Also, I always thought that USB drives come up as /dev/sdb, not /dev/sde.
When you plug in the USB drive, what node is created, sdb or sde? If sdb's created, it's a bug in the KDE media slave and you should be able to get around it by using the terminal.
If it's sde, the problem's a bit more complicated.

---

### Post by mctavish on 2005-10-12
aysiu, I've seen someone else with this problem too. You might want to raise a defect for it. As release time is coming up, it might be urgent if others are seeing this also. I can't confirm it because I don't use kubuntu.

The problem will I think be something to do with ivman, which (for kubuntu only - gnome has its own volume manager) automounts volumes and then starts a helper app - konqueror in this case.

I think ivman is for some reason misidentifying the volume name.

---

### Post by doctorphoton on 2005-10-12
i agree, i face the same problem.
in ubuntu usb is shown in desktop, but in kubuntu it is not on desktop.
me facing the same problem.

---

### Post by aysiu on 2005-10-12
It's now [Bug #17668](https://bugzilla.ubuntu.com/show_bug.cgi?id=17668), and you're right--I'm not the only one:

[http://kubuntuforums.net/index.php?topic=524.0;topicseen](http://kubuntuforums.net/index.php?topic=524.0;topicseen)

**Edit**: It's definitely a bug. I did a clean reinstall of Kubuntu Breezy and an apt-get upgrade (no universe repositories) and the problem was there again.

---

### Post by aysiu on 2005-10-15
**Update**: I upgraded to KDE 3.5 Beta, and the problem was solved.

---

### Post by isaidi on 2005-12-24
thanks for reporting this. 
I just downloaded and installed Kubuntu last night and did a world upgrade  ("world" from Gentoo) this morning, and i got this bug..

Disapointed, maybe i should have went with the standard Ubuntu Gnome... am Not getting a warm welcome from Kubuntu...

---

