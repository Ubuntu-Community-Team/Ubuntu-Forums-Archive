---
title: "can't umount/eject DVD except as normal user"
date: 2005-10-19
forum: Desktop Environments
---

### Post by meonkeys on 2005-10-19
When I put in a DVD it appears on the desktop. When I right-click on that DVD and select Eject, I get a popup titled "Eject Error", with a "Show more details" dropdown icon (a small triangle). When I click the icon, I see the following:

umount: /dev/hdd: not mounted
umount: /media/cdrom1: must be superuser to umount
umount: /dev/hdd: not mounted
umount: /media/cdrom1: must be superuser to umount
eject: unmount of `/media/cdrom1' failed

If I do 'sudo eject /dev/dvd' from a console, the DVD will eject.

Any idea why this won't work as a normal user? This worked fine in Fedora Core 4, if that helps.

---

### Post by end11 on 2005-10-22
Hey, I had this same problem. It's kindof ugly but i fixed it by changing the cd line in /etc/fstab to have users (with and s) instead of user.
So i changed 
```
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
to
```
/dev/hdb        /media/cdrom0   udf,iso9660 user**s**,noauto     0       0
```

This works because when you have just user, it only means that the same user that mounted it can unmount it, and the daemon that mounts it runs as root. Interestingly, this also fixed it so i can eject the cd by pressing the button on it now.

Hope that helps

---

