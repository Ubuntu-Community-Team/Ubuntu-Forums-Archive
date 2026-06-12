---
title: "Troubleshooting mounting smbfs"
date: 2006-01-15
forum: Desktop Environments
---

### Post by dgermann on 2006-01-15
Hi--

Not even sure where to start doing the troubleshooting here. Perhaps you can point me in the right directions.

I have a working Samba install on a server, called Samba1. (Creative naming, huh? ;)  ). I access it everyday for business purposes from Windows machines, both Win95 and WinXP Pro. No problems there. Samba1 is running RedHat 9.0.

I also have Samba1 set up to export files via NFS to another machine which runs an hourly backup of the server. No problem there. The backup machine is running Ubuntu 5.10.

The third machine I am trying to setup also is running Ubuntu 5.10. Its /etc/fstab is:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

//samba1/vol22        /sam/vol22  smbfs    rw,user,credentials=/root/.smbcredentials       0       0

//samba1/vol12        /sam/vol12  smbfs    credentials=/root/.smbcredentials
   0       0

# //samba1/sys2        /sam/sys2  smbfs    credentials=/root/.smbcredentials
   0       0

//samba1/doug2        /sam/doug2  smbfs    credentials=/root/.smbcredentials
   0       0

# //samba1/etc        /sam/etc  smbfs    credentials=/root/.smbcredentials
 0       0

# //samba1/vol22        /sam/vol22  smbfs    credentials=/root/.smbcredentials
     0       0

```

When the .smbcredentials file has my username and password, it mounts vol12, vol22, and doug2 without a problem, but the directories all appear with a lock symbol in File Browser, and I cannot save to these directories, although I can read from them and copy from them. It shows only vol22 on the desktop as an icon.

When the .smbcredentials file has root's username and password on Samba1, it mounts doug2, but fails on vol12 and vol22. The directory for doug2 shows the lock symbol and I cannot save to it.

On samba1, the rights for /doug2 are 700, for /vol12 are 755 and for /vol22 are 766, and the owners are doug:doug, apps:apps, and data:data. apps and data are groups, not users, on samba1; doug is a member of both those groups.

On the client machine, the rights for /sam/doug2, /sam/vol12, and /sam/vol22 are all 755 and the owner is root:root.

On the backup machine, which has these all mounted as nfs, the rights and owners are: /doug2 700, owner 500:500, /vol12 755, owner 510:505. /vol22 766, owner 511:504.

So: what steps would you take to try to get this net to working on the client machine?

Thanks for any hints you can give me!

---

### Post by dgermann on 2006-01-16
Hi--

OK, I found something that seems to work. Can anyone tell me if it is a mistake to do this?

I added ",uid=doug,gid=doug" to the options in /etc/fstab. Now the lock symbol is gone and I can edit files on the smbfs.

Was this a safe way to get access?

Thanks!

---

### Post by zoiks on 2006-01-16
There's nothing wrong with that IMHO.  This tells mount what user should be the "owner" of the data that is mapped.

---

### Post by dgermann on 2006-01-17
zoiks--

My concern was that every user was then seen as the user doug, with all the permissions of doug.

Today I tried something different. I set the fmask and dmask=775. The user doug is in the group root, so that user can access these files now and edit, but other users not. That seems a little more secure to me, yes?

Thanks, zoiks!

---

