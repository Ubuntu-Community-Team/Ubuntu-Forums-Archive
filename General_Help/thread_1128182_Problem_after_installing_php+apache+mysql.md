---
title: "Problem after installing php+apache+mysql"
date: 2009-04-17
forum: General Help
---

### Post by guja on 2009-04-17
Same problem had on 9.04 x86_64 and i386.

After I install php+apache+mysql, that applet in panel which shows my name and icon representing some from my current statuses from Pidgin goes crazy. All icons from statuses are black rectangles.

After I reboot, gmd doesn't start, but it says something like trying to read from some disk, something, but gdm won't rise. I have to login from console as user and do startx to get to desktop.

When I get there, Ubuntu says some fatal errors about that applet mentioned above and offers me to keep it or remove it from panel. What ever I choose, that applet is removed.

Wtf is happening?

---

### Post by Vadi on 2009-04-17
I can't confirm your findings here. Installed lamp via tasksel, verified that apache works. The FUSA applet was still working and after a reboot, GDM too.

Have any other info you can provide?

---

### Post by guja on 2009-04-17
This is what I get when I do reboot.

GDM doesn't start, but some weird loadings and then screen on which this is written (I managed to rewrite this):

```
[2.766433] i8042.c: No controller found.
Loading, please wait
19+0 records in
19+0 records out
kinit: name_to_dev_t (/dev/disk/by-uuid/6e7d94a8-d476-4548-b597-3e15a5919524) = dev(8,2)
kinit: trying to resume from /dev/disk/by-uuid/6e7d94a8-d476-4548-b597-3e15a5919524
kinit: No resume image, doing normal boot
Ubuntu 9.04 blackbox tty1
blackbox login:
```

Interesting thing is that I totally removed everything I did with apache2, mysql and php, but I still get the same screen when booting ^^.

---

### Post by guja on 2009-04-18
Okay, I see that no one gave any answers to this. Anyhow, I checked if all paths to /dev/sda* partitions were correctly written in /etc/fstab and everything there were okay.

Something probably happened when removing some mysql or php or apache related pkg and from some reason some some packages related to gnome-desktop were gone. That's why GDM didn't want to start.

Anyhow, I did:
```

sudo apt-get install gnome-desktop
```

rebooted, and everything went well.

Case closed.

---

