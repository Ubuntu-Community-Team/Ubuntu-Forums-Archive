---
title: "How to show only removable drives on desktop"
date: 2009-03-05
forum: Desktop Environments
---

### Post by ijustwantyourhalf on 2009-03-05
I am curious if anyone has figured out how to not show volumes that are listed in /etc/fstab but still show removable volumes on the desktop and places menu.

I have two partitions that I added after installing ubuntu. I mount them automatically  through /etc/fstab. They show up on my desktop and in my Places menu. I don't want that to happen because it confuses my users. They should experience these devices only seamlessly though their mount points in the filesystem.

I know how to show no mounted volumes on the desktop but that makes it so one has to go to a places menu (either on the panel or in a Nautilus window) to unmount flash drives or cameras. Also, showing no mounted volumes only applies to the desktop not the places menu.

This seems like it should be possible because the install partitions, the ones used by the initial ubuntu install, don't show up as mounted partitions on the desktop. Are these partitions flagged somewhere? Is this a fstab option, a gnome issue?

Thanks for any help,

Don

---

### Post by mcduck on 2009-03-05
Mount your internal partitions to any other place than /media. /mnt would be a good place, for example..

Only drives/partitions mounted in /media appear on desktop and in Places-menu. (of course if you mount your partitions to some other place you ca still add them to Places-menu as bookmarks, or create links to them in user's home directory to avoid having to always browse through the file system to access them.

---

### Post by ijustwantyourhalf on 2009-03-05
Thanks for the reply McDuck

My partitions are mounted in a subdirectory of my /home

This is what my fstab looks like.

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=76a05d6c-fd38-4a22-8a83-bb2d33f13217 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=6f3b64ab-5bce-45d9-8e25-40e81b4bf244 /boot           ext2    relatime        0       2
# /dev/sda4
UUID=930cb508-76d8-4836-801b-1025df2c9f07 /home           ext3    relatime        0       2
# /dev/sda3
UUID=175c2d90-7743-4375-aff5-979133d29ea4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1	/home/blue/Music/Music1			ext3	defaults	0	2
/dev/sda2	/home/blue/Music/Music2			ext3	defaults	0	2

Is it something in the "defaults" options or maybe not using UUID to identify the drives?

Edited to add: Tried adding UUID's to fstab, no change. Why do you think that my primary drives show up as sda in the fstab but sdb elsewhere? they were listed (e.g. in a "mount" command) as sdb and my secondary drives were listed as sda so I added the secondary to fstab as sda. But now I see that in fstab all the drives are listed as sda's and really identified by their UUIDs. Maybe this is the problem?

---

### Post by mcduck on 2009-03-05
Are you absolutely sure your mdrives are mounted corectly and as you specify in your fstab? Because anything mounted outside of /media really shouldn't get desktop icons. I can't really imagine any way how this would happen.

Please check that your drives are indeed mounting correctly, and that hey are not mounted in /media as well as/instead of the location you specify. If you have bad settings in fstab it might be that they are actualy automounted into /media..

Don't worry about the sda thing, probably your drive was recognized as the first drive during the install,a nd you have changed something after that. Some motherboards also have a nasty habit of recognizing drives in different order in every boot, and also plugging in removable drives may change things, This is why Ubuntu uses UUID's instead. Anyway, none of the mount settings for your drives actually include the sda part (apart from those you added yourself), they are just comments in the file to help you recognize which drive/partition is which.

If you want to be sure, mount your own partitions using UUIDs as well. That way it makes no difference if their device names change.

The "defaults" has no effect on this. Like I said, the only rule that determines if a drive is shown on desktop is if the drive is mounted in /media.

If this doesn't help solve your problem, please post here outputs of following commands:

```
sudo fdisk -l
blkid
sudo mount
ls /media
```

---

### Post by ijustwantyourhalf on 2009-03-05
Hi McDuck

I didn't know that a drive could get mounted twice (in /media _and_ where specified in /etc/fstab)

 Here is the output of those commands. I don't see anywhere the 160g drive is getting mounted twice but maybe I can't see it.

> blue@blue-desktop:~$ sudo fdisk -l
[sudo] password for blue: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008527d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9727    78132096   83  Linux
/dev/sda2            9728       19457    78156225   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009fab2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         127     1020096   83  Linux
/dev/sdb2             128        3951    30716280   83  Linux
/dev/sdb3            3952        4078     1020127+  82  Linux swap / Solaris
/dev/sdb4            4079       60801   455627497+  83  Linux


blue@blue-desktop:~$ blkid
/dev/sda1: UUID="c7dc7ac2-2cb7-46d0-bed0-f8b5ea3cf144" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda2: UUID="89f9c1aa-0de8-4ff3-a86a-8411a6d7de25" TYPE="ext3" SEC_TYPE="ext2" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="6f3b64ab-5bce-45d9-8e25-40e81b4bf244" TYPE="ext2" 
/dev/sdb2: UUID="76a05d6c-fd38-4a22-8a83-bb2d33f13217" TYPE="ext3" 
/dev/sdb3: UUID="175c2d90-7743-4375-aff5-979133d29ea4" TYPE="swap" 
/dev/sdb4: UUID="930cb508-76d8-4836-801b-1025df2c9f07" SEC_TYPE="ext2" TYPE="ext3" 


blue@blue-desktop:~$ sudo mount
/dev/sdb2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-13-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /boot type ext2 (rw,relatime)
/dev/sdb4 on /home type ext3 (rw,relatime)
/dev/sda1 on /home/blue/Music/Music1 type ext3 (rw)
/dev/sda2 on /home/blue/Music/Music2 type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/blue/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=blue)


blue@blue-desktop:~$ ls /media
cdrom  cdrom0




Any thoughts?

Don

---

### Post by Royle on 2009-05-18
I'm having the same problem. I have a partition mounted to /home/user/Music, and it's showing up as a mounted partition on the desktop and in places. It is not mounted in /media. Was this ever solved?

---

### Post by dodgefan on 2009-09-13
i would like to add to this as well as i have shared drives on a vista box mounted to my ubuntu box in fstab to directories in /home/user that show on the desktop as well but would like them to not be

also how do i show icons like Home and Trash?

---

### Post by TiredBird on 2009-09-14
Count me in as having a similar problem. I have 21 items that that are mounted via the --bind option. None of them is ever in /media and I am not mounting them in /media. They all come from a partition that is mounted on 'srv' and they all are mounted for final use in my home directory. How do I get rid of the 21 icons (they look like disk drives) on my desktop?

---

### Post by TiredBird on 2009-09-14
> **ijustwantyourhalf said:**
>  ... I know how to show no mounted volumes on the desktop... Don

Actually, if I just knew how to do the above I could probably solve my problem. Would you be willing to share your knowledge?

---

### Post by TiredBird on 2009-09-14
Found at least a partial answer in [this post]("http://ubuntuforums.org/showpost.php?p=7507701&postcount=5").

---

### Post by Wollombi on 2009-12-19
Yes, that will take ALL drives from the desktop, but it also hides flash drives and such and I want those to still show on the desktop when I plug them in.   Does anyone know how to ONLY show the removable media drives and not mounted hard drives?

---

### Post by Dfairlite on 2010-03-13
no fix yet huh? i have the same issue. I have created a new folder in my home folder so that i can give read/write access to people on the network. but they still show up on the desktop. checked media and they are not mounted there. they are just in my /home/drives folder i created.

---

### Post by biogsm on 2010-07-21
I found a solution:

[https://bbs.archlinux.org/viewtopic.php?id=45849](https://bbs.archlinux.org/viewtopic.php?id=45849)

---

### Post by matthanley on 2011-01-09
I'm having the same issue. Additionally, there are partitions that I specifically don't want to be visible, but they show up in the side pane.

Like several other posters here, I uncheckd the "visible" option in gconf-editor, but this only removes them from the desktop and not the side pane. Like the OP, I want my partition to be integrated seamlessly into the file system.

I looked at this entry: > **biogsm said:**
> I found a solution:
[https://bbs.archlinux.org/viewtopic.php?id=45849](https://bbs.archlinux.org/viewtopic.php?id=45849)
but there were two problems:
[LIST=1]
[*]According to the post, it's deprecated
[*]It didn't work for me
[/LIST]

Any other ideas? It seems like Ubuntu is trying to be too clever here.

---

### Post by matthanley on 2011-01-16
After messing around with hal for a long time, I'm starting to think that Nautilus doesn't pay any attention to what you do with it. I could see the changes I that made reflected in the Device Manager, but the unwanted directories were still showing up in the side pane.

I followed the directions in [this thread]("http://ubuntuforums.org/showthread.php?t=1496408") and after
[LIST=1]
[*]mounting all the partitions I *don't want to use at all* to /dev/null and
[*]mounting all the partitions I *do want* to directories in /mnt and symlinking to them from my home directory,
[/LIST]
I'm getting the behavior I wanted.

It would still be nice if I could just mount things wherever I want them and not have Nautilus figure out what it thinks I really mean, but this gets the job done well enough.

---

### Post by matthanley on 2011-01-16
After messing around with hal for a long time, I'm starting to think that Nautilus doesn't pay any attention to what you do with it. I could see the changes I that made reflected in the Device Manager, but the unwanted directories were still showing up in the side pane.

I followed the directions in [this thread]("http://ubuntuforums.org/showthread.php?t=1496408") and after
[LIST=1]
[*]mounting all the partitions I *don't want to use at all* to /dev/null and
[*]mounting all the partitions I *do want* to directories in /mnt and symlinking to them from my home directory,
[/LIST]
I'm getting the behavior I wanted.

It would still be nice if I could just mount things wherever I want them and not have Nautilus figure out what it thinks I really mean, but this gets the job done well enough.

---

