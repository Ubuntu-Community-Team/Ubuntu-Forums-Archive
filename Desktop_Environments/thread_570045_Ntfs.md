---
title: "Ntfs?"
date: 2007-10-07
forum: Desktop Environments
---

### Post by FreeThePenguin on 2007-10-07
Ok, i have windows and ubuntu installed... im having some trouble getting things working in ubuntu so im using windows for the time being, i have already setup NTFS partitions for my appz and games.  My question is how hard would it be to access (read/write) files on those NTFS partitions?  I have heard of people using FAT32, but i have large partitions, what do you guys think?

---

### Post by distroman on 2007-10-07
Use ntfs-config if you're working with large files fat32 won’t do it.
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html#more-143](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html#more-143)

---

### Post by lavinog on 2007-10-07
I'm a little confused about what you are doing with the ntfs partition?
are you looking to keep linux games on your ntfs partition?
if no, then why do you want read/write access?

My concern is that writing to ntfs partitions with linux was at one point a bit risky.
But there are ways to access an ext3 partition with windows...thus you can combine your linux documents folder with your my documents folder in windows.

---

### Post by mtbsoft on 2007-10-07
Just a note of caution.  I have noticed that VMWare w/s is very picky about "common" partitions.  I use player under 'doze and w/s on Ubuntu and I had to use a FAT32 partition to store the image on as it wouldn't work from Linux with an NTFS partition.

If you don't use VMWare then of course this won't apply but just be aware that there can't be issues with using NTFS from Linux.

---

### Post by distroman on 2007-10-07
I can’t really figure out what the OP intends either.
I have a shared ntfs partition (so it can be accessed with ease from both OSs) for music.

Good advice about “my documents folder” btw, should be on a separate partition so why not /home ;-)

---

