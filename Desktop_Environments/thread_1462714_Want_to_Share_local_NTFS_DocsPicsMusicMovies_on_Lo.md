---
title: "Want to Share local NTFS Docs/Pics/Music/Movies on Local Network"
date: 2010-04-26
forum: Desktop Environments
---

### Post by wdavro on 2010-04-26
I have 3 machines:[INDENT] Desktop: Core 2 Duo 2.8GHz; dual booting Karmic and XP; 2-1TB, 2-500MB SATA drives
Desktop: AMD Duron 1GHz; XP;  1-500MB, 1-250MB IDE drives
Laptop: Intel Centrino 1.8GHz; XP
[/INDENT]My goal is, on the Core 2, to have 1 central location for the Music, Movies, Docs, Pics, etc folders regardless of the OS I'm booted too.

Currently, on the Core 2, I have the following partitions:[INDENT] 2 EXT4 parts: 1 mounted at /, the other at /home
3 NTFS: 1 is the XP boot, 1 for movies and 1 for all other data
[/INDENT]I've been trying to figure out how to make Karmic share the local NTFS parts.  All weekend I've been reading and studying and experimenting.  Among the readings:[INDENT] Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009...ess-linux.html ]("http://blog.linuxtoday.com/blog/2009/08/painless-linux.html")
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.p...data+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Share Windows partition:
[http://lifehacker.com/348858/use-a-s...n-dual-booting]("http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting")
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)[/INDENT]I can get the local NTFS parts to mount, but I can't get to them from the XP desktop.  I tried mounting the NTFS in /media and then creating symlinks to them in my home folder (which is shared on the network).  But when I try to access the symlinks from my XP laptop or desktop I always get "access denied.  I've tried several different lines to mount one of the NTFS parts in fstab:[INDENT] /dev/sdd1       /media/NTFS-D1-1TB        cifs   credentials=/etc/.credentials.dt,rw,nocase,nobrl,uid=1000,gid=1000 0 0

/dev/sdd1       /media/NTFS-D1-1TB        cifs  user=me,password=hello,rw,nocase,nobrl,uid=1000,gid=1000 0 0

/dev/sdd1       /media/NTFS-D1-1TB        ntfs-3g user=me,password=Hello,rw,dmask=000,fmask=111,async,nodev,exec,nosuid,user 0 0

/dev/sdd1       /media/NTFS-D1-1TB        ntfs-3g user=me,password=Hello,rw,dmask=000,fmask=000,async,nodev,exec,nosuid,user 0 0

/dev/sdd1       /media/NTFS-D1-1TB        ntfs-3g user=me,password=Hello,rw,dmask=000,fmask=111,async,nodev,exec,nosuid,user,uid=1000,gid=1000 0 0

/dev/sdd1       /media/NTFS-D1-1TB        ntfs-3g user=me,password=Hello,rw,async,nodev,exec,nosuid,user,uid=1000,gid=1000 0 0
[/INDENT](Note: if there are any odd spaces in the above lines ex: asyn c, or g id, it's an artifact of this message system they are not like that in fstab; uid and gid=1000 are my id nbrs)

but no success.

I'd appreciate any ideas on how I can do this.

---

### Post by byStanderone on 2010-04-26
...would suggest using samba,..focus on that.

---

