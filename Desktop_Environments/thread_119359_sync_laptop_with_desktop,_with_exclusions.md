---
title: "sync laptop with desktop, with exclusions?"
date: 2006-01-19
forum: Desktop Environments
---

### Post by savage on 2006-01-19
Howdy all. I would like to get some suggestions for how best to handle this situation. Also if anyone has seen some howtos for this sort of thing, please throw me the links. What I want to do is create an automated syncing setup, whereby the /home directory on my desktop and the /home directory on my laptop are mirrored with certain exclusions, so I don't ever have to manually move files between the two.

I have Ubuntu desktop system, x86, fairly standard except the partitioning. There are two hard disks, the /home dir includes symlinks to the secondary hard disk which has a partition /data that holds all my large files and media. This makes it easy for me to backup my home directory to a usb stick, and to grow in the future, or install new OS. The laptop only has one hard disk, and will not be able to hold everything from the /data directory. However the laptop needs to receive certain directories that are located under the /data directory and most everything from the /home directory. I would like the symlinked directories to just be dumped as/into real directories on the laptop.

I'm looking at rsync and rdiff-backup over ssh with cron as possible solutions. Other concerns I have is with the hidden directories and system files under the /home directory since the systems are not identical. Also what happens if the laptop isn't on/plugged into the network when the cron runs? The laptop is ppc (if that has any bearing). The username is the same on both systems, and they are networked together via router/cat5. This will be the first time I've used rsync, or rdiff-backup, and tried automating something. Your input is appreciated, and I will be creating a howto out of this.

---

### Post by Spie on 2006-01-19
I think this will help you:
[http://ubuntuforums.org/showthread.php?t=15082]("http://ubuntuforums.org/showthread.php?t=15082")

I use it and it works very well.

---

