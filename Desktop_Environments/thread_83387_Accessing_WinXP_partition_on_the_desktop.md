---
title: "Accessing WinXP partition on the desktop"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Brennan on 2005-10-28
Hello everyone,

My problem is I'm trying to access my Windows XP partition that's mounted on the Ubuntu desktop, but when I click on it I get an error message saying I don't have enough permissions.  I went as far as adding my regular user to the group "root" and I still have this same error message coming up.  The only way I can access this partition is via command line.  Is or has anyone else had this problem and if so, is there a solution?  I even tried editing my /etc/fstab file using gid and umask which didn't work either.

Thanks in advance for any solutions to this annoying problem!

---

### Post by Remmelas on 2005-10-28
I'm not sure exactly what issue you have, it's odd that you can access via command line but not via gui.  to make it easy for a user to access (read/write) a windows partition(assuming it's not ntfs), just add 'user' to the fstab mount options, then mount it as the user that you want to be able to read it.

---

### Post by mfyahya on 2005-10-28
I have the same problem. I seen as 'sda2' icon on the desktop which is my windows ntfs partition, but I can't access it through the GUI or command line. I can browse the files however, if I go to System->Adminstration->Disks Manager and click the browse button on the Partitions tab

---

### Post by aysiu on 2005-10-28
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by Brennan on 2005-10-31
Ok, that worked!  I also noticed that as well, Mfyahya, about the disk partition way of seeing your Windows partition.

So as of this writing, my /etc/fstab looks like this:

/dev/hda1     /media/windows     ntfs     gid=users,nls=utf8,umask=0222     0 0

I think I probably would have gotten it working sooner if I would have restarted the system instead of editing fstab and then clicking on the icon for my XP partition to open up.

Thanks for all the help!:KS

---

