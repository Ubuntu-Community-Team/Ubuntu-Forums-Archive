---
title: "Reading ext3 partitions from windows"
date: 2009-03-08
forum: General Help
---

### Post by eks on 2009-03-08
Hello,

I had one hard disk that was dying, and recently bought a new 1tb one to replace it. Made four partitions on it, in this order:

. / with 16gb
. swap with 8gb
. /home with 560gb
. /backyard, formated with NTFS, with some 325gb

/backyard is mounted as F: on Windows. With the old hard disk I was using [http://www.fs-driver.org/](http://www.fs-driver.org/) without any problems, mounting /home on U:. It is actually still mounting the old hard disks (ext3) partitions, but not the new one. Actually, they mount, showing on windows exploder, but when I try to access it the OS asks the (*incredibly smart question*) to format it. :-#

The only thing that's different is that, on the new disk, there's a NTFS partition. On the old one there was not. Could that be the problem? Any possible workaround, instead of trying to format /backyard also as ext3?

Thanks!


Edit: problem was new default inode size of 256bytes of the new ext3 partition, whereas the previous default one was 128. 256b inodes are not supported by [ext2ifs]("http://www.fs-driver.org"), but are supported by [ext2fsd]("http://www.ext2fsd.com"). Or so it was, until I reinstalled windows and the latest version of ext2fsd now does not reads the partition it was reading before...

---

### Post by Schok on 2009-03-08
i use the ext3 reader from the same website and same error occurs (format the drive). According to the troubleshooting guide from the website, u need to install something, but that too, doesn't work for me. currently no ext3 reader can run on my windows, so im stuck with ubuntu reading ext3 and ntfs only.

---

### Post by eks on 2009-03-10
Thanks Schok! I forgot to check the troubleshooting page of fs-driver.org page, tried the mountdiag.exe there and had:

```

The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not
mount it because the file system has an inode size unequal to 128 bytes (inode
size: 256 bytes).
The only way to solve it is to back up the volume's files and format the file
system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all
backed-up files.
After that, the Ext2 IFS software should be able to access the volume.

```

Which after some googling got me to this thread:

[http://ubuntuforums.org/showthread.php?t=979523](http://ubuntuforums.org/showthread.php?t=979523)

It seems Intrepid's new default value for inodes is 256, instead of 128.

I can reformat my /home, but I rather have all features of Ubuntu instead of from Windows.

---

### Post by gladson1976 on 2009-03-27
hi all

i've been having the same problem and i've found a driver that works with ext3 with 256 byte inodes.

try the Ext2Fsd driver at
[http://ext2fsd.sourceforge.net](http://ext2fsd.sourceforge.net)
it works with both read and write support.

---

### Post by neilevan814 on 2009-03-27
Does that software work with Vista Home Premium by any chance?

Just figured I would answer my own question.  Just back from installing ext2fs on Vista for 2 ubuntu's 8.04 and 8.10 and a media partition.  All are permanently mounted as drives F: G: H: and are read and write.

---

### Post by TE0I0TEJIb on 2009-04-24
thank you very much
i had the same problem, but Ext2Fsd works great! and it has an utf8 encoding support!

---

### Post by ubu-for on 2009-04-24
You could also try this program.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by eks on 2009-09-12
fs-driver.org does not work any more for a new install of any linux distro since most of them format the ext3 partitions with inodes of 256 bytes, which is not supported by ext2ifs (fs-driver.org).

[ext2fsd]("http://www.ext2fsd.com") does support 256b inodes. Or at least it did...

I just reinstalled windows on a new disk, installed the latest version of ext2fsd and when I try to open my /home partition windows asks to format it, just like with ext2fs driver... Any ideas why??

---

### Post by eks on 2009-09-13
Downgraded from 0.48 version of ext2fsd to [0.46a]("http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/0.46a/Ext2Fsd-0.46a.exe/download") and now it works again.

---

