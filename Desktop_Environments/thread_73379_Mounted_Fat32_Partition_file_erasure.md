---
title: "Mounted Fat32 Partition file erasure"
date: 2005-10-08
forum: Desktop Environments
---

### Post by whitewizardcoder on 2005-10-08
Hello

I've been running Ubuntu Hoary on a dualboot machine w/ Windows XP.  I have both my primary and extended Windows drives (one for XP, the other for my files; both are FAT32) mounted with the options iocharset=utf8 and umask=000.  I wanted both to be rewritable by the user, and this seemed as if it were the only way to do so.  This works fine under Ubuntu, where I can read/write to these partitions, however, as soon as I boot to Windows, all of the files I added/modified are gone.  I also noticed that my USB drive (also FAT32) will read/write under ubuntu, but as soon as it's inserted into a Windows machine, all the modified files disappear.  The files that disappear do not appear again when I switch back to ubuntu, and file recovery software doesn't see them either.  Is there any way to fix this problem?

Thanks,
WhiteWizardCoder

---

### Post by loell on 2005-10-09
i have that same problem too, with my usb card reader, i drag files to the sd/mmc
but when i view the files to my phone, its not there, i think one way around this problem, is to invoke "sudo nautilus" in the command line and then you can drag files to the proper directories. IMHO

---

### Post by weizilla on 2006-03-25
I am having the same problem. I have a fat32 partition mounted via fstab for read and write. I then have gaim save all of its settings on that partition in linux. however, whenever I boot into windows then boot into linux, all of the files are missing. I still can't figure out what is wrong.

---

### Post by plewisfdx on 2006-04-07
Are you sure they are mounted when writing to the partitions?  

$ mount    <-- to find out

If they are not mounted, there will still be a directory saving the files, but not in the right place.  i.e.  I want /home/user mounted on /dev/hdd1, but its not mounted as I thought.  If I copy file.txt to /home/user it will copy the file, and a "ls" of /home/user will include file.txt.  If I then mount /home/user on /dev/hdd1, file.txt will "disappear".  Actually, Ubuntu won't "see" it since you mounted a partition over top of it.  If you "umount" the partition, the file will "re-appear".

Sorry if this was obvious, but this will result in the problem you described.

phil

---

