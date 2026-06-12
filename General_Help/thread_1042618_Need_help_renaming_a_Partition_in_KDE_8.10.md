---
title: "Need help renaming a Partition in KDE 8.10"
date: 2009-01-17
forum: General Help
---

### Post by Dieseler on 2009-01-17
Hello

I'm having a little trouble renaming a partition. Now it is simply labeled as Volume (ntfs) but I wish to name it Win XP.
I have installed ntfslabel and used it in terminal like this,

ntfslabel /dev/sdb1 Win XP
I also tried,
e2label  /dev/sdb1 Win XP

I saw Bhodi's guide to fstab and it mentioned creating a directory first but as it is, I can see it has a directory in /media as,
/media/disk, when it is mounted.
I also gksudo dolphin (graphically) created the folder Win XP in /media and tried the naming process again.

It doesn't seem to be taking an effect.
I've tried it with the disk mounted and unmounted and restarted.

If someone could give me an idea of what I might be doing wrong I would be real grateful.
Thanks.

---

### Post by Dieseler on 2009-01-17
I'm going to delete the line in fstab I have created and graphically delete the folder Win XP until someone can give me an idea where I'm failing here.

It would seem that since all I really want to do is rename the partition that there would be a way without an fstab entry, I dunno.

---

### Post by Dieseler on 2009-01-17
Wow,
All that head banging for nothing.

If you ever need to add a LABEL to a partition just use GParted.
If no one sees a problem with that call this one solved.

---

