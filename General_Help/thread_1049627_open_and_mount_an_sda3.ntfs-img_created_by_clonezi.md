---
title: "open and mount an sda3.ntfs-img created by clonezilla"
date: 2009-01-24
forum: General Help
---

### Post by baybe1111 on 2009-01-24
Hi, really stuck on this- so are others I think, but no replys for weeks.. trying to uncompress, mount and browse a backed up ntfs partition (made by clonezilla) from my laptop into my external USB drive. I've >80G free there and its ext3 format (NTFS partition was ~50 gig). Where clonezilla created the image is where I'm trying to extract it.

I get the error in the first attempt so I removed the .* as my images are single files, but the Permission Denied has me stumped- I'm using sudo- so I'm root right? OK so I try Sudo su for the third attempt and get unknown id and gzip errors as below...I get the feeling I'm missing something? 


 ls -l  sda3.ntfs-img
-rw------- 1 root root 7622235507 2008-12-27 21:13 sda3.ntfs-img

andrea@george-desktop:/media/disk/laptop/2008-12-27-11-img-just-b4-ibex-32-bit-install$ dir
disk Info-packages.txt sda1 sda-chs.sf sda-pt.sf
Info-dmi.txt NTFS sda2.ntfs-img sda-mbr
Info-lshw.txt parts sda3.ntfs-img sda-pt.parted
andrea@george-desktop:/media/disk/laptop/2008-12-27-11-img-just-b4-ibex-32-bit-install$ sudo cat sda2.ntfs-img.* | gzip -d -c | ntfsclone --restore-image -o sda2.img -
ntfsclone v1.13.1 (libntfs 9:0:0)
cat: sda2.ntfs-img.*: No such file or directory

gzip: stdin: unexpected end of file

andrea@george-desktop:/media/disk/laptop/2008-12-27-11-img-just-b4-ibex-32-bit-install$ sudo cat sda2.ntfs-img | gzip -d -c | ntfsclone --restore-image -o sda2.img -
ntfsclone v1.13.1 (libntfs 9:0:0)
ERROR(13): Opening file 'sda2.img' failed: Permission denied
andrea@george-desktop:/media/disk/laptop/2008-12-27-11-img-just-b4-ibex-32-bit-install$ sudo cat sda2.ntfs-img | gzip -d -c | ntfsclone --restore-image -o sda2.img -

 sudo su  cat sda3.ntfs-img | gzip -d -c | ntfsclone --restore-image -o sda3.img -
ntfsclone v1.13.1 (libntfs 9:0:0)
Unknown id: cat

gzip: stdin: unexpected end of file

---

### Post by VMC on 2009-05-22
Did you ever get your question answered?

Try this if your still looking:
cat sda2.ntfs-img.* | gzip -d -c | sudo partclone.ntfs -r -o /dev/sdx

---

### Post by Toon Macharis on 2009-11-14
Hi there, the first part and the last part in your command

> sudo su cat sda3.ntfs-img | gzip -d -c | ntfsclone --restore-image -o sda3.img -

are wrong

change

> sudo su cat sda3.ntfs-img into > sudo cat sda3.ntfs-img

and change

> ntfsclone --restore-image -o sda3.img - into > sudo ntfsclone --restore-image -O /dev/sda3 -

so in the last command:
1. you add sudo (so you don't get a permission denied error because you are not root)
2. you change the small -o (--output) to a big -O (--overwrite)
3. you change the name of your image sda3.ntfs-img to the partition you will write to, /dev/sda3

Before you do this, you need to have created the partition /dev/sda3 e.g. with fdisk and have it formatted to NTFS (type 7)

As an example, this is the command I ran myself and this would work for you as well:

> gunzip -c /home/toon/images/windows.img.gz | sudo ntfsclone --restore-image --overwrite /dev/sda1 -

---

