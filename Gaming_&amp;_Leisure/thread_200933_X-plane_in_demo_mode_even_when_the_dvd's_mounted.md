---
title: "X-plane in demo mode even when the dvd's mounted"
date: 2006-06-21
forum: Gaming &amp; Leisure
---

### Post by J@F on 2006-06-21
I can't get x-plane to find my dvd in dapper which it needs to take x-plane out of demo mode. the problem is x-plane looks for the dvd to be mounted on the following

/mnt/cdrom
/cdrom
/media/cdrom
/mnt/dvd
/dvd
/media/dvd
/mnt/x-plane
/mnt/xplane

but my dvd drive is mounted /media/dvdrecorder

so i need to symlink to one of the above directories

i can't figure out how to symlink. i've tried "ln -s /media/dvdrecorder /mnt/dvd" but that creates a symlink at /mnt/dvd/dvdrecorder not /mnt/dvd

please help i'm new to linux

---

### Post by tristan on 2006-06-21
I had the same problem, and the same lack of success trying to symlink. The secret is to actually create a new entry in your fstab file so that the DVD is mounted at /media/dvd:

sudo gedit /etc/fstab

Append this line to the end of the file
/dev/scd0     /media/dvd    udf,iso9669 user,noauto 0    0

I'm not sure what your system calls your DVD, it may or may not be scd0

Good luck! Xplane is an incredible game which I've wasted many happy hours on under linux

---

### Post by J@F on 2006-06-21
thank you for the quick reply.

I added the line to my fstab with the change to /dev/hdd and now it won't mount. isn't messing with ones fstab potentially dangerous.

anyone else know how to symlink it

edit: It works now. I had to create the /media/dvd directory. problem solved thanks a billion

---

### Post by paul_holmes on 2006-08-28
A workaround is to type sudo nautilus in a terminal. This will give you root privelages. If you right-click on the file /media/dvdrecorder you can select 'make link' from the menu. Just rename it /media/cdrom.

---

### Post by paul_holmes on 2006-08-28
A workaround is to type sudo nautilus in a terminal. This will give you root privelages. If you right-click on the file /media/dvdrecorder you can select 'make link' from the menu. Just rename it /media/cdrom or the link can now be cut and pasted to any directory.

---

### Post by YummyOlives on 2011-01-16
hi xplaners

same problem here with a little twist, 

i have xplane installed on the vista partition and not on the linux partition and launch it with wine1.3 with no problem but as i am not using my org. dvd and have downloaded iso.image to remove it from the demo mode, but i have tried whats been mentioned above and still it doesnt recover from the demo mode ; please advise 

xplane is in vista partition and
the iso.image is on the vista partition

now how to mount it properly, i have used gmount, gisomount,acetoneiso,furius iso, BUT no avial, 

any suggestions?

---

### Post by Perfect Storm on 2011-01-16
Necromancing. Thread closed.

---

