---
title: "How to disable the automatic mounting"
date: 2008-08-18
forum: Desktop Environments
---

### Post by alex_kde on 2008-08-18
Hi, I using 7.04 Feisty Fawn, installed with dual boot, when I start my session, on the desktop appear the icon of the windows device mounted, ready for use.

That's fine for me, but not for the others user I have on Ubuntu. 

I was trying to find a way to disable the automatic mounting of the windows device but, I wasn't able to find a way to do it.

My account is administrative, and I would be very gratefull for yours comments.

TIA

Alex.

---

### Post by cdtech on 2008-08-18
If it's mounted through /etc/fstab, it could be commented out. If I could see the device being mounted:
```
sudo fdisk -l
```
and the fstab:
```
sudo gedit /etc/fstab
```

---

### Post by Too Late on 2008-08-18
If the problem is that it appears to the desktop, it doesn't need to be uncommented. Just change the mounting point to somewhere else than /media/, eg. /mnt/windows (first you must manually make that folder). Then it will be mounted, but there's no icon on the desktop.

---

### Post by alex_kde on 2008-08-19
I changed the mounting point, and worked.

Thanks, that was good.

Now I wonder, Is there a way to run this mounting process just for me, but no for the other users, in a selective way.

I remenber , every user have a script which runs and configure each user's enviroment, like a session ini, and I want to know what and where is this script located, may be there I could manage the mounting process ? .

TIA,

Alex.

---

