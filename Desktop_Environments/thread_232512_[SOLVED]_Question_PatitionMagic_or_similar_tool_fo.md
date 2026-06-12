---
title: "[SOLVED] Question: PatitionMagic or similar tool for Linux?"
date: 2006-08-08
forum: Desktop Environments
---

### Post by wieman01 on 2006-08-08
Hey Folks, 

Would anybody know a Linux tool that does a job similar to PartitionMagic?

I want to partition my drives, resize them, possibly change the format of the file system, order, etc. I love PartitionMagic for its simplicity, but so far I am unware of a comparable tool under Linux.

Thanks, guys.

---

### Post by someguyouknow on 2006-08-08
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by SpongeBob SquarePants on 2006-08-08
Yep...you can use QT Parted, available either with a suite of utilities on the System Rescue Disk at.....

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

or individually at.......

[http://qtparted.sourceforge.net/](http://qtparted.sourceforge.net/)

---

### Post by RRS on 2006-08-08
[GParted]("http://gparted.sourceforge.net/livecd.php")
It's a live cd, about a 30mb download.

Nice graphic interface and able to perform the tasks you have in mind.

As a side note, I've heard that Partition Magic doesn't allways "play well" with Linux, never tried it myself though.

---

### Post by KillerKiwi on 2006-08-08
Im sure gparted is on the install disk...

Just boot it and run System -> Admin -> Partition Manager (I think)

---

### Post by etank on 2006-08-08
I don't know if it was an older version or not but I ran a gparted live CD on a Windows XP machine to resize a partition and it or something messed up the MBR. It was easy enough to fix by running ```
fdisk /mbr
```. Just thought that may be useful for anyone that uses this tool and runs into the same problem.

---

### Post by wieman01 on 2006-08-08
Great, guys. I will try it when I am back home. Since I don't have Windows any longer, GParted sounds to be a reasonable option. Thanks a lot.

---

### Post by suziequzie on 2006-08-12
> **etank said:**
> I don't know if it was an older version or not but I ran a gparted live CD on a Windows XP machine to resize a partition and it or something messed up the MBR. It was easy enough to fix by running ```
fdisk /mbr
```. Just thought that may be useful for anyone that uses this tool and runs into the same problem.

Thank you! I tried re-installing Kubuntu from a ship-it CD (graphical install) and it overwrote my MBR. I prefer grub on floppy. This fixed it right up. And such a simple command to remember too.
:grin:

---

### Post by wieman01 on 2006-08-12
> **suziequzie said:**
> Thank you! I tried re-installing Kubuntu from a ship-it CD (graphical install) and it overwrote my MBR. I prefer grub on floppy. This fixed it right up. And such a simple command to remember too.
:grin:

If you have an old Win98 CD, you can do this anytime you want. Just boot up the CD and run "fdisk".

---

