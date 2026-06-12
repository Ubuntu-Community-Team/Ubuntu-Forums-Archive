---
title: "HELP: Ubuntu tuneup and maintenance."
date: 2009-02-21
forum: General Help
---

### Post by amkr on 2009-02-21
How do I maintain Ubuntu? In Windows, I used to do stuff like:
1. Registry cleanup and defragment
2. Chkdsk
3. Disk defragment
4. Virus scan
and lotz more....How do I do all these in Ubuntu?;)

---

### Post by wangsuda on 2009-02-21
> **amkr said:**
> How do I maintain Ubuntu? In Windows, I used to do stuff like:
1. Registry cleanup and defragment
2. Chkdsk
3. Disk defragment
4. Virus scan
and lotz more....How do I do all these in Ubuntu?;)

To put it simply, you don't. You really don't need to. Yes, there is an anti-virus (clamtk - found in Synaptic), but you only really need it with a dual boot system (IMO).

---

### Post by baizon on 2009-02-21
> **amkr said:**
> How do I maintain Ubuntu? In Windows, I used to do stuff like:
1. Registry cleanup and defragment
2. Chkdsk
3. Disk defragment
4. Virus scan
and lotz more....How do I do all these in Ubuntu?;)

1. ```
sudo apt-get autoclean
``` or/and ```
sudo apt-get autoclean
``` and you have to delete the config manually.
2. [http://en.wikipedia.org/wiki/Fsck]("http://en.wikipedia.org/wiki/Fsck") (is integrated)
3. [http://www.novell.com/coolsolutions/qna/15032.html]("http://www.novell.com/coolsolutions/qna/15032.html")
4. [http://packages.ubuntu.com/intrepid/clamtk]("http://packages.ubuntu.com/intrepid/clamtk")

---

### Post by ajgreeny on 2009-02-21
```
sudo apt-get autoclean
```just removes un-needed package files from your cache; it does not quite do what the OP asked about. ```
sudo apt-get autoremove
``` will get rid of any unwanted and un-needed applications installed as dependencies of applications you have subseqwuently removed.  This may be what the second poster meant in the his second command shown.

1. Registry cleanup and defragment
2. Chkdsk
3. Disk defragment
4. Virus scan

1, 2 and 3,  Not needed at all.  The auto fsck filecheck every 30 boots does all that is needed.  There is no registry in linux to get bigger and bigger and slow the system down, and the ext3 linux file system does not fragment nearly as much as fat32 or ntfs.  I don't think there are any defrag apps for linux anyway.

4,  If you are running your system as a server from which windows users get files, mail, etc etc, then you might want to use clamav, the background application of clamtk mentioned above, but for a personal desktop there is really no need for a virus checking application.

The much easier general housekeeping of linux is one of its great plusses, as far as I'm concerned.

---

