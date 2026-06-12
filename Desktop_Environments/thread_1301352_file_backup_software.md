---
title: "file backup software"
date: 2009-10-25
forum: Desktop Environments
---

### Post by nmyrick on 2009-10-25
If anybody can find a decent Linux based backup software out there, please let me know.  I've tried several, and none of them seem to be worthwhile.

I've tried these:

File Backup Manager, SBackup, KDE Partition Manager, and a couple others, and none of them will do what I want them too.  

The best one I've found so far is SysBack, and that is a Windows based backup that can be run in Wine. However, it still doesn't let me do what I really want to do, which is to create a complete image of the active primary partition from within the Ubuntu Environment.  

This can be done in Windows with Acronis, so I would expect that it can be done in Linux as well, I just haven't found the software to do it.  Acronis will not run in Wine.

Any Help?

Thanks,
NCMyrick

---

### Post by ndefontenay on 2009-10-25
I think tar and rsync should be enough to handle all your backup needs. You just make a tar ball of the root folder you want to use and push it to your remote destination.

Is there any other requirements than this?

```
man tar
``` to see how it works

---

### Post by kellemes on 2009-10-26
For imaging..
[Partimage]("http://www.partimage.org/Main_Page")
[Clonezilla]("http://clonezilla.org/")

A tutorial that may be helpful.
[http://www.dedoimedo.com/computers/free_imaging_software.html]("http://www.dedoimedo.com/computers/free_imaging_software.html")

---

### Post by revanb on 2009-10-26
I've found that a good command line script is much more useful and customizable for specific backup requirements. I use rsync. 

I would suggest you look for information on the dd command. I think it can possibly help you.

Good luck!

---

### Post by revanb on 2009-10-26
For instance:

To duplicate a disk partition as a disk image file on a different partition

```
 dd if=/dev/sdb2 of=/home/sam/partition.image bs=4096 conv=notrunc,noerror
```


I have not tried this, it is from [http://en.wikipedia.org/wiki/Dd_%28Unix%29](http://en.wikipedia.org/wiki/Dd_%28Unix%29)

---

### Post by Sigma1 on 2010-05-11
I've had similar problems to the first post. The best so far appears to be NSSBackup. SBackup (simple backup) does not like writing on other disks, at least in 10.04. I also had a nasty surprise with the command-line backup-manager, which backed up /etc and then removed it from the boot disk, a problem which I haven't seen mentioned in forums but which simply stops your machine from starting (since the sudo id's are stored in /etc)! (Solution: boot from a LiveCD and restore your backup /etc files as sudo.) Back in Time backs up well enough, but doesn't compress anything, as far as I could see. NSSBackup is available here [https://launchpad.net/~nssbackup-team/+archive/ppa](https://launchpad.net/~nssbackup-team/+archive/ppa) with instructions for installation via Synaptics.

---

### Post by chiwi on 2010-05-12
+1 rsync

---

