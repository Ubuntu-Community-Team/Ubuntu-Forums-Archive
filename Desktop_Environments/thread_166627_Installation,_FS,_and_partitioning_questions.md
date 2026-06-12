---
title: "Installation, FS, and partitioning questions"
date: 2006-04-26
forum: Desktop Environments
---

### Post by sf. on 2006-04-26
I plan on setting up a new dual boot system with XP and Ubuntu and am looking for some help and advice on how to do it correctly (the first time).

-I'll have atleast two hard drives. Is it better to keep XP and Ubuntu on completely separate drives, or does it not matter at all?
-I'd like to have a partition that both OS's can read/write to. Would it be better to try to do this as NTFS or ext2? I think the file size limit makes FAT32 not an option. 
-How many partitions should be used for Ubuntu? Is it possible for these partitions to be hidden or completely non-accessible to XP? I guess this might depend on what I end up using as a solution for my previous question.

Any help with the above would be greatly appreciated and any other advice would be great too! :)

---

### Post by bluevoodoo1 on 2006-04-26
This resource has really helped me in the past...
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

It has many options for dual booting and the like.

---

### Post by gingermark on 2006-04-28
[QUOTE=sf.]
-I'll have atleast two hard drives. Is it better to keep XP and Ubuntu on completely separate drives, or does it not matter at all?
-I'd like to have a partition that both OS's can read/write to. Would it be better to try to do this as NTFS or ext2? I think the file size limit makes FAT32 not an option. 
-How many partitions should be used for Ubuntu? Is it possible for these partitions to be hidden or completely non-accessible to XP? I guess this might depend on what I end up using as a solution for my previous question.[/QUOTE]

Ok, sure a hard drive each makes things easier - you won't have to worry about resizing partitions if your needs change.

DO NOT USE NTFS - Linux is not reliable writing to that. There are drivers for XP that allow it to read ext2 (and 3, I think) so that would be a reasonable choice.

Ubuntu needs 2 partitions minimum - one for the swap partition, which is usually 1.5 - 2 times your RAM, and one for everything else. However you can have more. A lot of people choose to place their /home directory on a separate partition, as it makes resinstalling the OS easier.

Normally these drives won't be seen by XP. I don't know how using the ext2 driver on a shared drive would affect the visibility of the Ubuntu partitions, as I don't run Windows myself.

---

### Post by louis_nichols on 2006-05-01
I would also recommend using LVM. It seems difficult to understand at first glance (at least for me it was), especially because the documentation is pretty complete and I haven't had the luck to find short howto's or tutorials. But, once you get into it for a short while, you realize it's not hard at all and very useful.

You will be able to resize partitions (well... sort of equivalents of partitions) with two commands; and, using reiserfs as a file system, without even (un)(re)mounting (ext3 requires unmounting, so this means that making such changes to the partition where / is mounted requires booting from a liveCD or something like that). For example, when I installed Ubuntu, I gave it 15 GB. I first gave 2 GB to the partition for / and 3 for /home. Then I just resized them on the way, as needed, without a sweat. Just 2 commands in terminal. reiserfs saved me some [space,]("http://ubuntuforums.org/showthread.php?t=157647") too.

Also, you could later add a hdd to your hardware setup and incorporate all of it or just one or more partitions into the LVM, which can make all this space behave as only one partition. (LVM uses different terms, because it's also more complicated, (I dunno them all, even though I use LVM lol) but for ease-of-use I find associating these entities with partitions convenient)

Another advantage is that there is no driver for win to even read LVM, so that's safe.

Info [here]("http://www.tldp.org/HOWTO/LVM-HOWTO/"). I usually jump directly to part 11. :)

---

