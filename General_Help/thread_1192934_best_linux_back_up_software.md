---
title: "best linux back up software?"
date: 2009-06-20
forum: General Help
---

### Post by Arminius on 2009-06-20
I'm a linux newb, and I'm used to norton ghost 10 on windows, would let me back up the whole drive into a big file, then if I can't find a single file, so long as the software is installed on the system, I can reach into that image of the old drive and extract anything I like.

is there anything like that?

---

### Post by SuperSonic4 on 2009-06-20
I use luckybackup but that's a kde app I think

---

### Post by howefield on 2009-06-20
Clonezilla

[www.clonezilla.org/](www.clonezilla.org/)

Download and burn as a live cd, and is pretty similar to ghost.

---

### Post by Arminius on 2009-06-21
do I have to boot from clonezilla every time I want to restore a file from the old back up?

---

### Post by 3rdalbum on 2009-06-21
I've been reading and trying to get a definitive answer from the Clonezilla website, but I can't find out for sure.

Clonezilla should save a big "disk image" file, that is basically a byte-for-byte copy of your disk. I believe it may also compress the disk image so any big chunks of empty space don't actually take up space... it's difficult to explain this.

If you decompress the file to end off with a decompressed disk image, you can mount it on your desktop and access it as though it was an ordinary disk.

First you create a mount point (a place to mount it):

```
sudo mkdir /media/clone
```

Then you mount it:

```
sudo mount -o loop -t ext3 path_of_file /media/clone
```

IMPORTANT: Instead of literally typing "path_of_file", you need to type in the file path of the decompressed disk image, or drag the disk image to the terminal to automatically fill this in.

Note that I don't actually know anything about Clonezilla, and if someone with Clonezilla experience shows up and starts giving advice you should be taking theirs over mine :-)

---

### Post by mike555 on 2009-06-21
If you want you should be able to use "Reconstructor" to make a full ,bootable,installable DVD backup......
   or for timed backups you could use "BackInTime" from;   [http://backintime.le-web.org/](http://backintime.le-web.org/)   .............

---

### Post by Arminius on 2009-06-22
I ran clonezilla, yeah it only seemed able to make clones of hard drives, not what I was wanting which was just a single file with a hard drive in it.

---

### Post by moster on 2009-06-22
This maybe seems little stupid question, but why you do not manually copy all the sensitive files on another partition or external disk? You can always copy it back with ubuntu live disk even when computer do not boot.

---

### Post by Hallvor on 2009-06-22
There are many possibilities. I usually boot up a livecd and run partimage. I then copy the whole partition to a gzip file on my external hard drive.

---

