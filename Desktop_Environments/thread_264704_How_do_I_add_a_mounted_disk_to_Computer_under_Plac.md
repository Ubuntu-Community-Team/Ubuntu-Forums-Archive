---
title: "How do I add a mounted disk to Computer under Places menu"
date: 2006-09-25
forum: Desktop Environments
---

### Post by samssf on 2006-09-25
I've screwed around with my fstab file and with dmraid trying to add two drives on Raid 1 to my Ubuntu system.

The two HDDs used to show up under Computer in places menu (not mirrored) but now they dont show up at all. Ultimately I need my raid 1 set up, but for now... what I want to know is what causes the drives to be listed in Computer.

If I have a partiion mounted, and I want it to show there, what do I do?

Thanks.

---

### Post by bernied on 2006-09-25
Is it possible that you just need to mount it in /media (not in /mnt)?

---

### Post by samssf on 2006-09-25
They are actually mounted in media.. because when I try to mount them again it says already mounted at /media/sda1 , etc

---

### Post by bernied on 2006-09-25
I found this:
```
sudo /etc/init.d/dbus-1 restart
```
here:
[http://ubuntuguide.org/wiki/Dapper#How_to_refresh_Places_menu_in_GNOME_.28if_mounts_to_.2Fmedia.2F_in_.2Fetc.2Ffstab_does_not_show_up.29](http://ubuntuguide.org/wiki/Dapper#How_to_refresh_Places_menu_in_GNOME_.28if_mounts_to_.2Fmedia.2F_in_.2Fetc.2Ffstab_does_not_show_up.29)

---

### Post by samssf on 2006-09-26
It worked! Greatly appreciated!

Note to anyone else who has this problem:

I did have to remove the -1  from the above command for it to work... *shrug*

---

