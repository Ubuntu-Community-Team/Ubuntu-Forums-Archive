---
title: "How to disable showing of mounted volumes on Desktop and in Nautilus sidebar?"
date: 2010-05-01
forum: Desktop Environments
---

### Post by Osm on 2010-05-01
Hi everybody!
I have a bit unusual request.
There are three partitions on my hard drive. Two of them were assigned to mount points / and /home during system installation. The third one was left intact.
After installation the first two partitions were automatically integrated into directory tree and there was a shortcut on the Nautilus sidebar for the third one. Then, I registered the third partition in /etc/fstab for automounting at /home/user/Data directory.  For now it works fine, the volume is mounted on startup. But I still have the shortcut to this volume in Nautilus sidebar and icon on my Desktop.
I am interested, if it is possible to disable showing of this items on Desktop and in Nautilus to make the third partition look like registered at system setup time.

Thank you in advance.

---

### Post by Bobhuber on 2010-05-01
> **Osm said:**
> Hi everybody!
I have a bit unusual request.
There are three partitions on my hard drive. Two of them were assigned to mount points / and /home during system installation. The third one was left intact.
After installation the first two partitions were automatically integrated into directory tree and there was a shortcut on the Nautilus sidebar for the third one. Then, I registered the third partition in /etc/fstab for automounting at /home/user/Data directory.  For now it works fine, the volume is mounted on startup. But I still have the shortcut to this volume in Nautilus sidebar and icon on my Desktop.
I am interested, if it is possible to disable showing of this items on Desktop and in Nautilus to make the third partition look like registered at system setup time.

Thank you in advance.
The easiest way to disable the desktop icon and be able to do a LOT more via GUI is to load Ubuntu Tweak. As far as not showing in the Nautilus side bar I've never heard of that before.It sort of defeats the purpose of Nuatilus as a file manager. I mount my extra partitions in fstab just FOR that purpose.

---

### Post by Morbius1 on 2010-05-01
Anything mounted in /media or in /home/your_user_name will show up under places and on the desktop.

Anything mounted to /mnt or in "/" itself ( like /windows, for example ) will not.

---

### Post by Osm on 2010-05-01
Morbius1, thanks for explanation. 
It seems I just need to remount partition into the right place :)

---

