---
title: "How to automount (pmount) at startup instead of at logon"
date: 2007-03-09
forum: Desktop Environments
---

### Post by Underpants on 2007-03-09
Right now, I have a USB disk called "lacie-usb" that gets mounted automatically when I log into gnome. 

Is there a way to make this automatic mount occur without me logging in? Sometimes I reboot my system, or it never gets logged into and the drive isn't mounted, but I've got rsync snapshots going to it.

---

### Post by taurus on 2007-03-09
You can add an entry in /etc/fstab 

```
gksudo gedit /etc/fstab
```
so it would be mounted automatically each time you boot your machine (without logging in first).

```
/dev/sda1   /media/lacie-usb   vfat   iocharset=utf8,umask=000   0  0
```

---

### Post by Underpants on 2007-03-09
That's kind of a catch-22... If I set it up that way, that particular disk won't auto mount if I just stick it in while the computer is running, right?

---

