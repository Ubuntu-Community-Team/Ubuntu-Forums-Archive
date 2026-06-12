---
title: "unionfs-fuse and /etc/fstab"
date: 2011-12-30
forum: Desktop Environments
---

### Post by dentaku65 on 2011-12-30
Hi,

I'm trying to link multiple folder into a single mount point via unionfs-fuse.

My idea is about to have **Ubuntu One** and **Dropbox** into a single directory(space); I've been able to create in console without issue.
First I've created the mount point:
```
mkdir $HOME/MyCLOUD
```
Then launch the unionfs-fuse:
```
unionfs-fuse $HOME/Dropbox=rw:$HOME/Ubuntu\ One=rw $HOME/MyCLOUD
```
All is well. I can see the content of both cloud services in a single disk and if I copy some files, the files are correctly updated to the distinct services (upon the directory I choose).

For instance I've applied a green emblem on Dropbox directories in order to distinguish them from the directories of Ubuntu One.

[IMG]http://oi40.tinypic.com/rbz78n.jpg[/IMG]

I've try to put the whole thing in /etc/fstab in order to have MyCLOUD disk/space mounted at the beginning but without luck; in fact adding this on /etc/fstab:
> unionfs-fuse#/home/sava/Dropbox=rw:/home/sava/Ubuntu\ One=rw /home/sava/MyCLOUD fuse cow,allow_other 0 0
And giving a sudo mount -a command I receive this error:
> [mntent]: line 25 in /etc/fstab is bad
Does anyone knows hot to configure unionfs-fuse in fstab?
I really puzzled on it.

TIA
Den

---

### Post by satanselbow on 2011-12-30
> **dentaku65 said:**
> 
Does anyone knows hot to configure unionfs-fuse in fstab?
I really puzzled on it.


I quick google of "union-fs fstab" threw up this: [https://grangerx.wordpress.com/2010/12/31/using-fuse-unionfs-with-centos-5-5-i686/](https://grangerx.wordpress.com/2010/12/31/using-fuse-unionfs-with-centos-5-5-i686/)

---

### Post by dentaku65 on 2011-12-30
> **satanselbow said:**
> I quick google of "union-fs fstab" threw up this: [https://grangerx.wordpress.com/2010/12/31/using-fuse-unionfs-with-centos-5-5-i686/](https://grangerx.wordpress.com/2010/12/31/using-fuse-unionfs-with-centos-5-5-i686/)

Thx for using google for me :-)

If you read the article, this folk speaks about unionfs (/usr/bin/unionfs) that do not exist anymore on Ubuntu since Lucid I guess, not unionfs-fuse; unionfs-fuse# <with_parameters> did not work as I post on #1

---

### Post by satanselbow on 2011-12-30
> **dentaku65 said:**
> I guess, not unionfs-fuse; unionfs-fuse# <with_parameters> did not work as I post on #1

Sigh...

Didn't look at any of the other results either then...

I don't think you can use the "$HOME" variable in fstab anyway, can you?

---

### Post by dentaku65 on 2011-12-30
> **satanselbow said:**
> Sigh...

Didn't look at any of the other results either then...

I don't think you can use the "$HOME" variable in fstab anyway, can you?

Correct; it is wrong to use $HOME in /etc/fstab, but I've already tried with full path; does not work too.

---

### Post by dentaku65 on 2011-12-30
Ok, solved...

even if not in elegant way, I mean without fstab

Extract my $HOME full path:
> $HOME = /home/sava/
Then edit rc.local
```
sudo gedit /etc/rc.local
```
And add these lines at the end:
> #Create MyCloud
unionfs-fuse -o allow_other -o cow /home/sava/Dropbox=rw:/home/sava/Ubuntu\ One=rw /home/sava/MyCLOUD

exit 0
Make rc.local executable:
```
sudo chmod +x /etc/rc.local
```
Reboot.
Now I have my single cloud point mounted automatically with the two services on it (Ubuntu One and Dropbox).

I considering this solution partial, because the goal was to use the fstab.

---

### Post by sisco311 on 2011-12-30
You have to replace the space in the path with \040:
```
unionfs-fuse#/home/sava/Dropbox=rw:/home/sava/Ubuntu**\040**One=rw /home/sava/MyCLOUD fuse cow,allow_other 0 0
```

---

### Post by dentaku65 on 2011-12-30
> **sisco311 said:**
> You have to replace the space in the path with \040:
```
unionfs-fuse#/home/sava/Dropbox=rw:/home/sava/Ubuntu**\040**One=rw /home/sava/MyCLOUD fuse cow,allow_other 0 0
```

Thanks! It works flawelessy.

Just for completeness, it is necessary to add *fuse* in /etc/modules in order to have unionfs-fuse capable to mount fuse filesystems

---

