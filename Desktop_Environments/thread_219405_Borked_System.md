---
title: "Borked System"
date: 2006-07-19
forum: Desktop Environments
---

### Post by cyricthemad on 2006-07-19
Ok, this has been a really friggin long day ](*,) .  At this point I just want to get my files from my linux partition and start over.

I have two physical hard drives.  Right now, hda is my Windows drive.  hdb is my ubuntu drive.  It is formated as 1 -> ext3, 2 -> extended, 5 -> logical lvm.  I have tried installing ubuntu again onto hda and mounting hdb into that and pulling my files, reloading grub, gag, and live cds (xubuntu, ubuntu, dsl) to no avail.  The closest I have gotten is from the 5.10 install cd rescue boot option.  From there I can at least see my files and I know they are there.  Unfortunately, I don't know how to... rescue them.

Any assistance at all would be greatly appreciated.

---

### Post by cptnapalm on 2006-07-19
where are you trying to rescue them to?  If to the Windows partition, then you're going to have a problem as the NTFS writing is pretty much a no go.

If you have a cd burner and you can load up Ubuntu, then you should be able to burn them if you can see them.

---

### Post by cyricthemad on 2006-07-19
Sorry forgot to mention.  On my windows drive, I have a large (enough for the files) fat32 partition.  Problem being, I do not know how to copy them in from the lx drive to the fat drive in the rescue.  I've tried mounting it, but no go.

As stated before, booting linux does not allow me to see these files, just the rescue option.  Whenever I try to mount anything from hdb I get an "already mounted or busy destination" message.

---

### Post by orlox on 2006-07-19
How did you try to mount it?

I mount my fat32 partition with the command:

sudo mount -t vfat <your FAT32 partition> <A FOLDER TO MOUNT IT>

for example, my FAT32 partition is /dev/sda3, and the folder I mount it to is /media/sda3, so the command is:


sudo mount -t vfat /dev/sda3 media/sda3

---

### Post by cyricthemad on 2006-07-20
Don't know what the deal was, but it finally accepted the mount, and I was able to recover all of my data.  Well, this weekend brings the joy of getting Ubuntu fully operational... again. :-({|=

---

