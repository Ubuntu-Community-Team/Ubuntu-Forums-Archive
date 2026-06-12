---
title: "The disk automount system has changed its behavior"
date: 2020-09-09
forum: Desktop Environments
---

### Post by jrrpnani on 2020-09-09
Let's see if anyone can give me a hand. I just made my user backup with BackinTime (an rsync manager) to an external hard drive formatted in NTFS. Before upgrading to Ubuntu 20.04 I have made my copies like this for months. The difference I have found is that now files with 'rare' characters for example 'Microsoft Corp.' (it finishes in point, a folder of fonts) and similar situations (folder Wine) now give me error and it cannot copy them. I smell that it has to do with as it reads the system the device NTFS and as it handles it
I have achieved that the folders created in my NTFS external hard disk manually mounted (I plug the disk to the system, it detects it, I unmount it, and I mount it by hand) do not give me that problem, so the issue is in how the system mounts them automatically. When I mount it manually I only indicate sudo mount /dev/sdc1 /media/user/disk without any option, I don't put anything special.
Any suggestions as to why you might have changed the behavior of the external disk after updating the system?

PD: I have it in NTFS to be able to take information to teams with guin2

---

### Post by TheFu on 2020-09-09
_Back in Time_ cannot use NTFS storage to create proper hardlinks.  It requires Linux file systems to work correctly.  
*Back in Time* is really a hardlink manager more than an rsync manager.  Hardlinks are are Unix capabilities.  Further, POSIX permissions, users, groups, ACLs are part of backups. Generally, Linux access to NTFS storage doesn't support those things.

---

### Post by jrrpnani on 2020-09-09
But the strange behavior to which I make reference is that before the update to version 20.04, the sessions of BackinTime worked well so much with the same hard disk NTFS, like with Ubuntu 18.04. In fact the files that now give me error, I already have them in previous copies of the program.
The difference of mounted hard disk are:
mount by the system
'mount | grep /dev/sdc2' show:
/dev/sdc2 on /media/nani/Disco_Externo type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
if I mount the disk:
/dev/sdc2 on /media/nani/DE type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
Maybe this can help with the problem

---

### Post by TheFu on 2020-09-09
I've never use udisks/2.  Mounting NTFS needs more control for my needs.  I use **autofs**, which uses the automounter, with these options:
```
/misc/250G -nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0002,dmask=0002    LABEL=250G
```
In the autofs config file, only 1 line is allowed for each entry.  autofs mounts storage upon request, which is good for USB and networked file systems. When no more files are "open" on the autofs mount, it will be umounted. This frees system resources when they aren't actually used.

For a manual mount, this would be the command:
```
sudo mount -o -t ntfs \
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002 \
 LABEL=250G  /misc/250G
```
I split the mount line into 3 lines using continuation characters to improve readability here. That's perfectly valid in any shell. Just be 100% certain there aren't any spaces after the '\' character or it won't work.

I'm mount to /misc/250G using the partition LABEL "250G" so I don't care about the device.  A UUID for the partition could be used as well, but we humans remember labels easier.  The options can be looked up in the mount.ntfs manpage, if you like.  The big_writes and async are to improve performance.  The windows_names option is to prevent any directories and files from having names that MS-Windows cannot support. The other options are for security reasons.  My uid and gid are 1000 for each, which is just a coincidence, but extremely common.  Check using the 'id' command.  For NTFS, permissions can only be set during the mount. This is a huge failure when it comes to backups.

If you have any interest in using autofs, there is a guide here: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
Just be aware that "automount" is a specific technical term that applies to using amd, autofs, automounter and not some GUI magical tool.

GUI programs often break standard stuff.  Perhaps udisks2 has broken something here?

---

### Post by jrrpnani on 2020-09-11
I have solved the problem adding an entry to fstab:

/dev/sdc2  /media/nani/Disco_Externo  ntfs-3g  users,noauto,uid=1000,user,rw  0 0

It's all about user permissions that had change in any moment.

---

### Post by TheFu on 2020-09-11
> **jrrpnani said:**
> I have solved the problem adding an entry to fstab:

[COLOR="#FF0000"]/dev/sdc2[/COLOR]  /media/[COLOR="#FF0000"]nani[/COLOR]/Disco_Externo  ntfs[COLOR="#FF0000"]-3g[/COLOR]  users,noauto,[COLOR="#FF0000"]uid=1000,user[/COLOR],rw  0 [COLOR="#FF0000"]0[/COLOR]

It's all about user permissions that had change in any moment.

Comments about the "**red**" stuff:

/dev/sdc2 - devices change order from time to time.  This is likely to break. The correct way is to use either the partition LABEL or UUID.  The UUID won't change from boot to boot regardless of the device name.  Uncover the current device name TO UUID mapping using the **blkid** command.

**ntfs-3g** is the F/LOSS implementation of the NTFS file system.  For a long time, it is exactly the same as **ntfs** as far as fstab is concerned. 
```
$ ll /usr/sbin/mount.ntfs*
lrwxrwxrwx 1 root root 13 Jun 20 11:58 /usr/sbin/mount.ntfs -> mount.ntfs-3g*
lrwxrwxrwx 1 root root 12 Jun 20 11:58 /usr/sbin/mount.ntfs-3g -> /bin/ntfs-3g*
```
They point to exactly the same tool.

Efforts are happening now by the company behind the proprietary NTFS driver to be included in the Linux kernel.  They've submitted their code and it has been rejected twice with cleanup comments. 
[https://www.phoronix.com/scan.php?page=news_item&px=Paragon-NTFS3-V3-For-Linux](https://www.phoronix.com/scan.php?page=news_item&px=Paragon-NTFS3-V3-For-Linux)  Slightly interesting, but probably unimportant to us. The kernel reviewers have criticized it again, so the 4th attempt may be forthcoming.

You probably looked up the "users" and "user" options already.  If "**users**" option is used, then there is little reason to also have "*user*" option. Having both is an opportunity for confusion and odd SW bugs to be encountered.  Probably don't want to have *uid=* option specified either.

I always have to look those up in the mount manpage:

```

       user   Allow an ordinary user to mount the filesystem.  The name of the
              mounting  user  is  written  to the mtab file (or to the private
              libmount file in /run/mount on systems without a  regular  mtab)
              so  that  this same user can unmount the filesystem again.  This
              option implies the options noexec,  nosuid,  and  nodev  (unless
              overridden   by  subsequent  options,  as  in  the  option  line
              user,exec,dev,suid).

       users  Allow any user to mount and to unmount the filesystem, even when
              some other ordinary user mounted it.  This  option  implies  the
              options  noexec,  nosuid, and nodev (unless overridden by subse&#8208;
              quent options, as in the option line users,exec,dev,suid).

       owner  Allow  an  ordinary user to mount the filesystem if that user is
              the owner of the device.  This option implies the options nosuid
              and  nodev  (unless  overridden by subsequent options, as in the
              option line owner,dev,suid).
```

With this information, I'd **sudo mkdir /media/Disco_Externo** and use:
```
UUID=xxxxxxxxx-yyyyyyy  /media/Disco_Externo  ntfs  users,noauto,noatime,async,big_writes,windows_names,rw  0 2
```
There are good reasons to avoid /media/{username} directories, mainly because other tools on desktop systems think they control those areas. If those tools get confused, bad things can happen.  

Those numbers at the end of each line in the fstab matter too.
```
       The sixth field (fs_passno).
              This field is used by fsck(8) to determine the  order  in  which
              filesystem  checks  are  done at boot time.  The root filesystem
              should be specified with a fs_passno of  1.   [B]Other  filesystems
              should  have  a fs_passno of 2.[/B]  Filesystems within a drive will
              be checked sequentially, but  filesystems  on  different  drives
              will  be  checked at the same time to utilize parallelism avail&#8208;
              able in the hardware.  Defaults to  zero  (don't  fsck)  if  not
              present.
```
2 is the correct answer.

---

