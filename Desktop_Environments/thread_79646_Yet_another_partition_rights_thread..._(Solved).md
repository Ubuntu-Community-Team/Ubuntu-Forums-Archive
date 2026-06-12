---
title: "Yet another partition rights thread... (Solved)"
date: 2005-10-20
forum: Desktop Environments
---

### Post by PtS on 2005-10-20
I'm trying to get the rights to some partitions that i share with windows on my father's computer. In /etc/fstab I've changed the ntfs partition's options to nls=utf8,umask=0222 and the fats to iocharset=utf8,umask=000 just as I did in my computer and like everybody has explained... I still don't have the rights to readonly the ntfs and read/write to the fats. I've noticed that the file systems are /dev/sdaX instead of /dev/hdaX. May that cause the problem?

/etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda9       /               reiserfs defaults        0       1
/dev/sda6       /boot           ext2    defaults        0       2
/dev/sda8       /home           reiserfs defaults        0       2
/dev/sda10      /media/musik    vfat    iocharset=utf8,umask=000        0       0
/dev/sda5       /media/program  vfat    iocharset=utf8,umask=000        0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222        0       0
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Jenda on 2005-10-20
You can't have write permission on NTFS. Linux just can't do that out of the box. There are, however projects that are attempting to do this. I do not know how for they are. You'll have to search.

---

### Post by PtS on 2005-10-20
I know I can't get write permission on NTFS... What's worse is that i can't get the READONLY permission either... And I can't get READ/WRITE permissions on my FAT.

---

### Post by audax321 on 2005-10-20
Your mount looks right...

Try this in a terminal:

sudo umount /dev/sda1

then

sudo mount /dev/sda1

Are there any error messages?

Type dmesg and check the last few lines for errors as well.

---

### Post by PtS on 2005-10-20
No errors while unmounting/mounting...
The last lines in dmesg is:

[4294742.675000] eth0: no IPv6 routers present
[4303276.746000] NTFS volume version 3.0.
Any clues?

---

### Post by audax321 on 2005-10-20
The only thing else I can think of is:

1. Does /media/windows exist?
2. What are the permissions on that folder?

  On my NTFS mount the permissions while unmounted are: 755
  and while mounted are: 555

If you want to try recreated the mount open up a terminal and do the following:

sudo umount /dev/sda1
sudo rmdir /media/windows
sudo mkdir -p /media/windows
sudo chmod 755 /media/windows
sudo mount /dev/sda1

If that doesn't work, I have no idea what is going on unless the partition is corrupt. Sorry. :confused:

---

### Post by PtS on 2005-10-20
Suddenly I've got readonly permissions on windows... the remaining problem is the fats... any ideas?

---

### Post by audax321 on 2005-10-20
Okay for the FAT32 partitions, I used to get an error saying that utf8 is invalid and not recommended when booting up with Hoary, so I always mounted them with just the umask=000 option. Try that and unmount/remount them.

---

### Post by manicka on 2005-10-20
try an entry like this 

/dev/sda10 /media/musik vfat defaults,rw,umask=000 0 0

---

### Post by PtS on 2005-10-20
None of them works... 
Does anybody have any more ideas? :???: 
Does anyone know why it is sda instead of hda? Maybe the solution is in there...?

---

### Post by Jenda on 2005-10-20
BTW sorry about my earlier post. I failed to notice the "'t" part of can't. I'm of no help in this thread...

---

### Post by audax321 on 2005-10-20
What happens when you access /media/musik and /media/program under Linux? Any error messages, etc. 

Also, not sure what happened with the NTFS partition but you can try recreating the FAT32 mounts as well by doing:

sudo umount /dev/sda10
sudo rmdir /media/musik
sudo mkdir -p /media/musik
sudo chmod 755 /media/musik
sudo mount /dev/sda10

AND

sudo umount /dev/sda5
sudo rmdir /media/program
sudo mkdir -p /media/program
sudo chmod 755 /media/program
sudo mount /dev/sda5


Also, normally drives that are denoted as sda instead of hda are SATA drives (any maybe RAID?). Drives that are hda are usually PATA drives.

---

### Post by PtS on 2005-10-20
Thanks!
Really... Ubuntu would be unable to use without you guys... without this forum...
Ok... maybe there are other forums...
Thanks.:D

---

