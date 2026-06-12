---
title: "help! i lost my ubuntu due to fsck..."
date: 2006-08-21
forum: Desktop Environments
---

### Post by slowlearner on 2006-08-21
i need help please.

just earlier, during bootup i was prompted to run fsck manually. I did it and anwered yes to all the questions thinking It would fix the disk inconsistency.. But to my horror, I discovered i lost everything.. Grub is gone!, I thought i could boot ubuntu from my windows box using grub for dos, but eventually failed because it can't find the kernel... what should i do?? I have my thesis in ubuntu and my defense is almost only 2 weeks from now... can somebody help me?? I need to recover my files...:( help! :(

---

### Post by peabody on 2006-08-21
> **slowlearner said:**
> i need help please.

just earlier, during bootup i was prompted to run fsck manually. I did it and anwered yes to all the questions thinking It would fix the disk inconsistency.. But to my horror, I discovered i lost everything.. Grub is gone!, I thought i could boot ubuntu from my windows box using grub for dos, but eventually failed because it can't find the kernel... what should i do?? I have my thesis in ubuntu and my defense is almost only 2 weeks from now... can somebody help me?? I need to recover my files...:( help! :(

Do you have the Live CD handy?  Are you able to boot it and view your files?

---

### Post by slowlearner on 2006-08-21
nope... i dont have a cd here to boot it,, I installed ubuntu usinga a harddrive installation... but i know the files are still there.. theres nothin wrong with the partition table.. I can still see the files with testDisk... will i be able to reinstall ubuntu without the new installation deleting the old files??

---

### Post by peabody on 2006-08-21
> **slowlearner said:**
> nope... i dont have a cd here to boot it,, I installed ubuntu usinga a harddrive installation... but i know the files are still there.. theres nothin wrong with the partition table.. I can still see the files with testDisk... will i be able to reinstall ubuntu without the new installation deleting the old files??

When you say that grub is gone, do you mean it doesn't load, or it won't boot Ubuntu?  If you don't have a cd, I recommend burning one, you should always have a boot cd handy for when these things happen.

As for reinstalling, your home folder should be fine, but you can never be too careful about these things.  Especially if you slip up and repartition when you don't need to.

---

### Post by akshaysrinivasan on 2006-08-21
May be you can install it on another partition and then access your files.Mind you the disk numbers are confusing.Oh and i have heard of a program called linux explorer which can read files from an ext3 fs partition
from windows.

---

### Post by slowlearner on 2006-08-21
Grub is completely gone.. And I've also checked my HDD again, and found out all my files are in the lost-and-found directory... what does this mean??

---

### Post by greatmetal on 2006-08-21
If linux explorer supports it I would copy all the files to windows
and just get them out of there

[http://ubuntuforums.org/showthread.php?t=189509](http://ubuntuforums.org/showthread.php?t=189509)

---

### Post by Ramses de Norre on 2006-08-21
If you're lucky they are still readable but the files in lost+found are mostly corrupted.. lost+found is the directory where fsck dumps all corrupted files..
Did you run fsck on a mounted partition??(= bad idea!)

I once encountered this too and my system was so hosed that I had to reinstall, luckily I had a seperate home partition which was intact..

I guess your best bet is trying to backup all files you need to another hard drive or a cd using a live cd and then reinstalling ubuntu..

---

### Post by slowlearner on 2006-08-21
great! just super! is it always this bad being a complete noob?
anyway, i've found an [app;](http://www.data-recovery-software.net/Linux_Recovery.shtml) It recovered my java files perfectly(they were all i needed).. Now, i guess i don't have any choice but to reinstall my ubuntu... Thanks for the help guyz.. :)

---

### Post by peabody on 2006-08-21
> **Ramses de Norre said:**
> If you're lucky they are still readable but the files in lost+found are mostly corrupted.. lost+found is the directory where fsck dumps all corrupted files..

...


To my knowledge what's in lost+found are files that were in the filesystem and have a link count greater than 0 but do not have any directory entries.  Whether or not they're corrputed is incidental.  If I am wrong about this I would love to be set straight as the lost+found is something I don't think I've ever completely understood.

The hardest part about dealing with what's in lost and found is the fact that the file's location and name have been hosed, so the only way to get any idea of what a file is and where it should belong, is to look at it or run the file command on it which guesses the filetype from magic numbers.  For instance, if running "file <file>" on one of the files produces something like this:

```

<file>: x86 boot sector

```

You know you've found a kernel image.

---

