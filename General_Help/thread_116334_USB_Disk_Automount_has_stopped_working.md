---
title: "USB Disk Automount has stopped working?"
date: 2006-01-12
forum: General Help
---

### Post by Lem on 2006-01-12
I've got a USB hard disk that has been working fine for months and months. happily automatically mounting itself whenever I plugged it in and even giving me a nice desktop icon to access it with.
Suddenly it's stopped mounting in Ubuntu. Works fine when I plug in my XP laptop, but in Ubuntu.. nowt.

Any ideas?

---

### Post by kaamos on 2006-01-12
Check if gnome-volume-manager is running. This takes of automounting.

---

### Post by Lem on 2006-01-12
[QUOTE=kaamos]Check if gnome-volume-manager is running. This takes of automounting.[/QUOTE]

Checked that one.. seems to be running

---

### Post by Lem on 2006-01-12
Can manually mount, but gnome-volume-manager doesn;t seem to be doing it's thing anymore. Have tried re-installing it.. still the same. Weird.

---

### Post by Lem on 2006-01-12
.

---

### Post by joris.brus on 2006-01-12
go to system -> preferences -> removable drives and media

not sure if you tried that already

---

### Post by Lem on 2006-01-24
This is still driving me mad. Why has it just decided to stop working all of a sudden? Can manually mount, but then only root has write permissions..

Grrr.. 

Help!

---

### Post by BruschiOnTap on 2006-01-24
I have the same problem with mine!  It won't automount, but when I manually mount it I am not allowed to write to it.  What gives???

---

### Post by Burning Bronx on 2006-01-25
You won't be able to write with normal mount, try using pmount instead. As for the automounting - I can't get mine runnin' either.

---

### Post by cbudden on 2006-01-25
One of my USB devices decided to stop mounting, but my digital camera and usb memory didn't.  Then the other one decided to start mounting again.

---

### Post by Who on 2006-01-25
Yep - same here, one of my devices no longer mounts automagically - others do! 

I haven't done any digging yet, but I will do tonight and report back

---

### Post by Lem on 2006-01-25
Any help on pmount? I tried it and couldn't open the drive, let alone write to it?

---

### Post by WirelessMike on 2006-01-26
If you have pmount installed, try taking the usb info out of your /etc/fstab file (don't have to tell you to make a backup first).

pmount is supposed to automount without fstab entry or media directory.

---

### Post by hornett on 2006-01-26
Yep this is broken now on both my machines (even on one with a custom 2.6.15 kernel). Hoping for a fix soon! :confused:

---

### Post by Who on 2006-01-26
Should one of us post a bug report?

---

### Post by Mustard on 2006-01-26
This won't help with the automount problem, but I've been using this command in terminal to mount my usbdrive for some months now. :)

```
sudo mount -t vfat /dev/sda1 /media/usbdrive -o user,uid=1000,gid=1000
```

This will mount with ownership being assigned to the first user account (which is most people by default)  so you can access the drive.  You would have to substitute your own /dev/devicename and /media/mountpoint instead of mine.  I've been having this issue for a long time now.  There are other threads around talking about the problem.

In another thread (somewhere out there), a suggestion was made to edit /etc/group and add 'hal' to the end of the group concerned with mounting USB drives which I believe is 'plugdev'.  I have no idea whether this will help.

---

### Post by hornett on 2006-01-27
[QUOTE=Who]Should one of us post a bug report?[/QUOTE]
[https://launchpad.net/distros/ubuntu/+bug/29888](https://launchpad.net/distros/ubuntu/+bug/29888)

---

### Post by hornett on 2006-01-31
Sorry to bump, but I'm wondering if any of you had found a miracle cure?

Cheers ;)

---

### Post by breezyfox on 2006-03-07
Hi
I just installed dapper and all my windows partitions that were mounted befour and shown on desktop just disapeared.
Dapper is not showing mounted hda1,hdb,hda2 etc on desktop. only USb drive is shown on desktop which is as befour.
while posting this reply i tried putting my CD in cdrom. it is ok and is showing on desktop.

bz

---

