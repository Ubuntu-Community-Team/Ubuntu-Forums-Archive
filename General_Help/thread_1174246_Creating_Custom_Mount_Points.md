---
title: "Creating Custom Mount Points"
date: 2009-05-30
forum: General Help
---

### Post by mypulitzer on 2009-05-30
Hello,

I have a pretty simple question (I think) concerning the creation of custom mount points.

I recently installed Ubuntu Netbook Remix with the following partition scheme:

/sda1 150mb /boot
/sda2 2gb   swap space
/sda3 18gb  / (Ubuntu system)
/sda4 extended partition
/sda5 8 gb  /documents (custom mount point)
/sda6 60gb  /stuff     (custom mount point)
/sda7 40gb  /shared    (custom mount point)
/sda8 20gb  /misc      (custom mount point)

After installing I learned (through exploration) that when you create custom mount points, the partitions are mounted in the main file system--ie. they appear in "/"

I'm curious as to whether or not there is any benefit to the creation of custom mount points. In other words, if I was to use the same partition scheme and just leave the mount points for sda5-sda8 (above) blank, would the file system work just as well. Would sda5-sda8 then show up as separate drives from "File System"?

On another note, I've set up my partitioning scheme like this to keep all my personal files (movies, music, documents, etc.) separate from the main File System. All I want on the File System is Ubuntu itself, configuration files (ie. /home), and installed apps. 

So I guess my question is, at the core, should I leave sda5-sda8 as they are with custom mount points (/documents, /stuff, /shared, /misc) or (I'm planning to do a clean install soon, mind you...) should I partition them as without any mount points? As a separate note (which may or may not matter) I am the only one who uses my system and I use it mostly for internet browsing and writing.

Thanks for your time,
B

---

### Post by sisco311 on 2009-05-30
> **mypulitzer said:**
> 

I'm curious as to whether or not there is any benefit to the creation of custom mount points. In other words, if I was to use the same partition scheme and just leave the mount points for sda5-sda8 (above) blank, would the file system work just as well. Would sda5-sda8 then show up as separate drives from "File System"?



There is only one filesystem. You can't leave the mount points blank. You can't access a partition until it's mounted. You can mount a partition wherever you want. The "traditional" locations  for data partitions are /mnt and /media. i.e. /media/Music or /mnt/Videos...

I prefer to keep my staff in my home directory so I have a separate /home partition.

Others prefer to keep they data separated from the home directory ( or home partition). They usually mount the partition(s) under /mnt/data or /media/data or directly in their home directory: /home/username/data.

---

### Post by ajgreeny on 2009-05-30
I think it would be easier if you just made a separate partition for /home at installation into which your user config could go, and another separate partition called data, which you would need to mount at boot time using a line in /etc/fstab.  If you mount the data partition in /media/data it will show with an icon on your desktop, or at least it would in an ordinary ubuntu system, not sure about the netbook remix.  The extra line in fstab should be something along the lines of ```
/dev/sda# /media/data ext3 defaults 0 1
```

---

