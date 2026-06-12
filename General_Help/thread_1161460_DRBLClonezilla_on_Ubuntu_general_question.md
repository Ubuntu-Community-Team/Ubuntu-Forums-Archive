---
title: "DRBL/Clonezilla on Ubuntu general question"
date: 2009-05-16
forum: General Help
---

### Post by Predatorian on 2009-05-16
hello buntuers,

ive been using remastersys to make an all-in-one recovery disk out of ubuntu for work since i cant find a distribution with all the stuff i want. i wanted to install clonezilla, but i had to use drbl. my question is, can i use drbl like i do with clonezilla live, and backup/restore systems with a live disk made from remastersys, or is it only usable on a server? if this doesnt make any sense, i probley didnt word it right.

---

### Post by quixote on 2009-05-16
I *think*, I'm not sure, that Clonezilla Live is just a subset of drbl.  So anything you can do with Live you can do with drbl.  (But not the other way around, of course.)  I'm just guessing, though, based on the last time I used C-zilla a couple of months ago, so don't bet the farm on what I'm saying!

---

### Post by logos34 on 2009-05-17
I think it's only server or live cd...Why not just use Partimage?

---

### Post by Predatorian on 2009-05-17
ill try out partimage

---

### Post by Predatorian on 2009-05-17
i found a bunch of tutorials on partimage, but the only thing i dont like is that it only does partitions, whereas clonezilla does the whole disk. a question then i have about that is, would i have to format the disk before i use partimage to restore an image?

---

### Post by logos34 on 2009-05-17
> **Predatorian said:**
> would i have to format the disk before i use partimage to restore an image?

no, with Partimage you can restore a partition without touching the rest of the disk.

I just got done restoring a backup of my root to it's original space, a logical partition on sda6.  Everything else is left as is.

One of the advantages of clonezilla is that it does entire disk and disk-to-disk mode (and even has a restore-iso-script to make a cd).  But for the entire disk you could simply use dd command...I.e. either

> [Cloning an entire hard disk:]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")
Code:

dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror

/dev/sda is the source. /dev/sdb is the target. Do not reverse the intended source and target. It happens. Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.

or compressed:
> 
To create a zipped hard drive backup image:

# dd if=/dev/hda | gzip > /mnt/hdb1/system_drive_backup.img.gz

Here dd is making an image of the first harddrive, and piping it through the gzip compression program. The compressed image is then placed in a file on a separate drive. To reverse the process:

# gzip -dc /mnt/hdb1/system_drive_backup.img.gz | dd of=/dev/hda

only disadvantage is that dd copies all sectors, even unused (unlike partimage and clonezilla, which copy only used.  BTW clonezilla uses partimage to copy linux-type formatted partitions)

---

