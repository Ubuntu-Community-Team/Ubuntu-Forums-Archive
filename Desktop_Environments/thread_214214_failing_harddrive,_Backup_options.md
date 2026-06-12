---
title: "failing harddrive, Backup options"
date: 2006-07-12
forum: Desktop Environments
---

### Post by dcstimm on 2006-07-12
hey guys, I have a severly damaged harddrive, It is 300gb and I know dd bs=512 if=/dev/hda of=/my/other/harddrive/blah.image conv=noerror,sync would get everything and skip over the bad sectors, but is there a way with dd to just grab the information on the drive and not the whole file system?  since the filesystem is 300gb?  I only have 80gb used on the drive and my backup drive is only 200gb, thanks!

cp -a locks up with I/O errors.  Thanks guys!

---

### Post by dcstimm on 2006-07-12
Anyone know?

---

### Post by jonrkc on 2006-07-12
I'm not certain I understand exactly what you want, but if it's to salvage all the actual data on the drive, and not copy blank sectors (such as partimage would do), the little script below should work.  I got it from a forum a long time ago.  The remarks explain the unusual option involving single dots.  In this example, I copy my /home/jon files to a flash drive.  Altering the script to read "/" instead of "/home/jon" should copy every file on the disk to whatever backup location is chosen.

I have a feeling this may not be what you want, though, since you're knowledgeable about the dd command, and that means you're no beginner. :)


```

mount /dev/sda1
cd /home/jon/
cp -rupv ./* ./.[^\.]* /usb_flash/jon/
#
#
##Note: the "[^\.] prevents cp from interpreting the "hidden file attribute" dot as 
#either the "current directory" dot or one of the "parent directory" dots by
#specifying that the second character is not to be a dot.  For this reason no
#file should begin with two dots, normally.

```

---

