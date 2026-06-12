---
title: "Mounted Drives Icon"
date: 2007-01-20
forum: Desktop Environments
---

### Post by falconisthebest on 2007-01-20
hi,

I have 2 drive partitions that are other than the system files drive, and the whole time they are mounted, their i con appears on the desktop, the same thing happens when i put a CD in, or plug a flash memo. an icon come to the desktop. is their a way to disable that. 

thanks for the help...

---

### Post by mcduck on 2007-01-20
If you want to remove icons for _all_ mounted drives, including CD's and USB drives, here's how to do it:

1. press Alt-F2 and run 'gconf-editor'
2. Browse to apps/nautilus/desktop
3. unmark the 'volumes_visible'

If you only want to remove hard drive icons from desktop, but wish to keep icons for CD's and portable drives you need to edit /etc/fstab to mount those drives anywhere else than in /media. I recommend /mnt..

---

### Post by falconisthebest on 2007-01-21
thanks mcduck, 

i will do that, i will let you know if it doesnt work out

appreciate the help

---

### Post by cendant on 2007-01-21
I was wondering - my internal CD-ROM is broken and I do not want to see it's icon on the Desktop. But I want to see other drives on it.

So, I should mount it to /mnt instead and it won't be shown by gnome-volume-manager?

---

### Post by ubername on 2007-02-11
> **mcduck said:**
> If you want to remove icons for _all_ mounted drives, including CD's and USB drives, here's how to do it:

1. press Alt-F2 and run 'gconf-editor'
2. Browse to apps/nautilus/desktop
3. unmark the 'volumes_visible'

If you only want to remove hard drive icons from desktop, but wish to keep icons for CD's and portable drives you need to edit /etc/fstab to mount those drives anywhere else than in /media. I recommend /mnt..

Stunning! Just what I wanted. I'll close my other thread asking much the same thing.

---

### Post by sillybuggers on 2008-03-08
> **mcduck said:**
> If you want to remove icons for _all_ mounted drives, including CD's and USB drives, here's how to do it:

1. press Alt-F2 and run 'gconf-editor'
2. Browse to apps/nautilus/desktop
3. unmark the 'volumes_visible'

If you only want to remove hard drive icons from desktop, but wish to keep icons for CD's and portable drives you need to edit /etc/fstab to mount those drives anywhere else than in /media. I recommend /mnt..

I have tried this.

I dont want to see my HD partition but want to see my CDROM etc but it doesnt seem to work.

no matter where i mount them they dont appear when I clear the Volumes_visible flag and when its in place I see the HD icon

---

