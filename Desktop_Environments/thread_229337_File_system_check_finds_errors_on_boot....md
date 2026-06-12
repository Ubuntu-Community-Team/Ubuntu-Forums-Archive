---
title: "File system check finds errors on boot..."
date: 2006-08-04
forum: Desktop Environments
---

### Post by Lufbery on 2006-08-04
Hi all,

I'm mostly new to Ubuntu, and new to Linux. 

Last month I bought a second hard drive for my computer and partitioned it roughly into thirds, with three 40 GB partitions. The first two are FAT32, and the last I left alone.

Then I installed Ubuntu 5.04 (Hoary?) on the 3rd partition. That one got three EXT3 partitions. The first of 10 GB got the root (/) files, the second of 25 GB got the /Home files, and the third got /Tmp files.

Everything worked well and I was able to duel boot just fine.

Then I tried to upgrade from Ubuntu 5.04 to 5.10 (Breezy?). That didn't go very well despite my attempts to follow the directions here to the letter.

So I figured that, since I didn't have any personal data on the Linux drives, I should just install 6.06 (Dapper?). I downloaded the ISO file and overwrote my previous installation.

I did everything basically the same, except that the third EXT3 partition was set as the Linux Swap instead of /Tmp.

I'm still able to dual boot with Windows, and everything works just fine. Except that I now get a disk error during boot up, when the file system is checked.

I've looked for a boot log so I can post the error here, but I haven't found one. 

The error basically says that there's an error in the MBR (but it doesn't indicate in which disk); there is space for so many clusters (it gives a number), but the disk has (and it give another, slightly larger number) clusters. I think the difference getween the two is 8 clusters.

How can I capture the exact error?

How can I fix it?

Thanks,

-Drew

---

### Post by Lufbery on 2006-08-16
As an update, I ran fsck and it found the same errors. I thought I fixed them, but on the next boot, they were still there.

The errors I got were on my DOS partitions. I didn't have them when I was running Hoary, so I'm not sure why I have them now.

I've done some searching in this forum and found similar threads, but the preferred option seems to be to disable the file checking on boot-up.

There's got to be a better option.

Is there?

Regards,

-Drew

---

