---
title: "ubuntu desktop not working..."
date: 2006-07-31
forum: Desktop Environments
---

### Post by sitric on 2006-07-31
i have a dual boot ubuntu and winXP both on different physical HDDs.windows is on hda and linux is on hdb and grub resides on hda0 i think(on the MBR). Now while i was in windows i tried to resize the ubuntu ext2 partition a bit and tried to make about 10GB of space from the allotted 40 for linux...
now something went wrong a PQ Partition Magic froze.... i had to force quit the program and next time i tried to boot into linux... the usual loading screen comes.. but then it starts force checking the hdb and then after around 69.8% start showing the block numbers real fast... then the screen goes blank or i am left on a command line a root, where i cannot login to my account or use apt-get to reinstall ubuntu-desktop....
then i installed [FSdriver]("http://www.fs-driver.org/index.html") in windows to read ext disks... all the data is in place.. whats wrong?

PS: if i copy the entire 10GB data and then install ubuntu again and put everything back.. will it work? also when i try to check for errors on hdb0 it tells me that the ext2 filesystem is corrupt!

---

### Post by OpsVentus on 2006-07-31
You can try to restore the partition table without formatting. Then try to repair it. Then resize again.
But if your thinking about reinstalling Ubuntu then this will all take a lot of time.
Partitioning and formating the disk and then installing Ubuntu is way faster.

It all depends on if there's data/settings on the Ubuntu disk you want to keep.

ps. I would never advise to resize, partition, format, or anything in that nature onder windows. Linux got way better tools for that.

Cheers,
Bart.

---

### Post by sitric on 2006-07-31
i want to keep all the stuff...
i have installed so many things from the repositories in that disk...
now what is the Exact procedure you are describing?
like from where to restore the partition table and how to repair it.
PS: you didn't mention if the 2nd method of copying all the data will work or not. will it? (not considering the time required)

---

### Post by OpsVentus on 2006-07-31
I wouldn't want to copy corrupt data. It's very uncertan if it will work depends on what's corrupted.

1 Don't use the disk, don't mount it, nothing!
2 Boot from a live cd, prefferable GParted one([http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828))
3 Put all your partitions in the way they used to be. Without formatting!
4 Check and repair everything with "e2fsck -f -y /dev/hda1"
5 Try to mount it and read it.
6 Try to boot from it.
7 If this dosn't work you can try to recover some data from the disk.

Good luck,
Bart.

---

### Post by sitric on 2006-07-31
ok.. now downloading GParted... will inform you if this fixes it...

i think the problem is that ubuntu cant mount the full volume (the last 30%) which i was trying to part....

EDIT: "e2fsck -f -y /dev/hdb1" worked flawlessly for me under GParted and took SEVERAL hours to rebuild the filesystem... finally "the file system was modified".

Cheers.
PS: Ubuntu works again!

---

