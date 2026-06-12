---
title: "Phantom Partition in &quot;Places&quot;"
date: 2011-11-08
forum: Desktop Environments
---

### Post by RMOP on 2011-11-08
I'll try to give some context which may shed light on how this anomaly came about.

I initially set out to automount my NTFS Data partition, which is shared between W7 & Ubuntu. At first I tried the "NTFS Configuration Tool," which did create an automount line in my fstab file, but it didn't do quite what I wanted. I finally solved the problem by manually entering the following line in fstab:

UUID=A04A69F04A69C41E	/media/NTFS\040Data	ntfs-3g	auto,users,uid=1000,gid=100,dmask=027,fmask=137,UTF-8	0	0

After then HIDING my W7 System partitions via these entries:

/dev/sda2 /Windows/sda2 ntfs defaults,umask=777 0 0
/dev/sda3 /Windows/sda3 ntfs defaults,umask=777 0 0
/dev/sda1 /Windows/sda1 ntfs defaults,umask=777 0 0

I found that my "Places" menu was cleaned up by the removal of the annoying entries for the W7 System partitions. Nice.

However, I also noticed, about that time, that there are TWO (2) entries for my NTSF Data partition in "Places." And, while the names are the same ("NTSF Data") the associated icons are different. More to the point, one entry appears to be broken, which I have called a "phantom," while the other is functional.

When I hover the pointer over the "phantom" NTSF Data icon, a text bubble appears with "Mount NTFS Data." If I click the icon, an error message invariably appears telling me "Unable to mount NTFS Data" "because the NTSF volume is already exclusively opened." I believe I get the same message even when the NTSF Data volume is NOT mounted (can't test now, as FireFox profile resides on that partition).

If I hover the pointer over the OTHER NTSF Data icon in the "Places" menu, the text bubble says merely "NTFS Data" and if clicked, opens a view of the drive in Nautilus.

I don't know what the non-functional "Places" entry represents, nor do I know how to get rid of it.

FWIW: when I open Nautilus to /media, there is a single entry for NTSF Data, but also a file titled ".created_by_python-fstab" the contents of which are a single line: "/media/NTFS_Data" which I suspect got added when using NTSF Configuration Tool, but that's a guess. I haven't yet deleted the file, as I don' know why it's there.

I'd appreciate any advice on running this thing to ground.

Many thanks.

---

### Post by mcduck on 2011-11-08
Could you please run the following commands in a terminal and post the output here with the contents of your fstab so we can have a bit more detailed look on your partitions:
```

sudo fdisk -l
blkid
ls -l /media
```


Anyway, the most likely reasons for a drive appearing twice is that you've changed the mount location of a drive but haven't deleted the old mount point, or that you have configured a drive in fstab and created a new mount point for it, but there is an error in the fstab entry so the drive gets automounted instead.

(related to the second possible reason, is the extra space in the middle of the "UTF-8" option in your fstab line just a typo in this post, or is that space actually there in your fstab?)

---

### Post by RMOP on 2011-11-08
Thanks for the reply. I agree that this looks like a residual from a previous mount, but I can't understand why it persists.

1) there is no space in the UTF-8 option in my actual fstab file. The space in the post seems to have been introduced by the forum interface, as it was pasted from fstab, and there is NO space there.

2) here are the commands and output:

~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90daee92

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         153     1228941    7  HPFS/NTFS
/dev/sda2             154       37640   301113105    7  HPFS/NTFS
/dev/sda3           37641       38915    10241437+   7  HPFS/NTFS
/dev/sda4           38916       60802   175799297    f  W95 Ext'd (LBA)
/dev/sda5           38916       54626   126190592    7  HPFS/NTFS
/dev/sda6           60680       60802      975872   82  Linux swap / Solaris
/dev/sda7           54626       60680    48626688   83  Linux

Partition table entries are not in disk order

~$ sudo blkid
/dev/sda1: LABEL="SYSTEM_DRV" UUID="32FA995FFA992061" TYPE="ntfs" 
/dev/sda2: LABEL="Windows7_OS" UUID="FC429E72429E317E" TYPE="ntfs" 
/dev/sda3: LABEL="Lenovo_Recovery" UUID="F22AA4FD2AA4BFC9" TYPE="ntfs" 
/dev/sda5: LABEL="NTFS Data" UUID="A04A69F04A69C41E" TYPE="ntfs" 
/dev/sda6: UUID="d6d254c0-fc97-4a07-b03e-8d4d114505a9" TYPE="swap" 
/dev/sda7: UUID="3aa8a07d-d2d5-4779-8a8e-7f17ff37783e" TYPE="ext4"

~$ ls -l /media
total 4
drwxr-x--- 1 myuserid users 4096 2011-11-07 15:30 NTFS Data

---

### Post by RMOP on 2011-11-09
Any further thoughts on this? I wouldn't ordinarily nag, but you distinguished yourself by your assistance in my other post about hiding partitions...

---

### Post by mcduck on 2011-11-09
Could you give your fstab as well? And there seems to be some things in /media that aren't shown in your post, so perhaps *ls -la /media* output would also be useful...

What happens if you comment out the line about the NTFS Data partition from your fstab? Does it still get mounted, and do you still see it twice? What directories you have in /media if you do that?

---

### Post by RMOP on 2011-11-09
> **mcduck said:**
> Could you give your fstab as well? And there seems to be some things in /media that aren't shown in your post, so perhaps *ls -la /media* output would also be useful...

What happens if you comment out the line about the NTFS Data partition from your fstab? Does it still get mounted, and do you still see it twice? What directories you have in /media if you do that?

Interesting. If I comment out the referenced line in fstab, the NTFS drive doesn't automount, but appears in "Places" and can be mounted from there. The PHANTOM NTFS Data entry is GONE. If I uncomment the line and reboot, automount resumes and the PHANTOM returns. Forgot to look at /media w the line commented out...later.

~$ ls -la /media
total 16
drwxr-xr-x  3 root    root  4096 2011-11-09 17:24 .
drwxr-xr-x 26 root    root  4096 2011-11-07 23:28 ..
-rw-r--r--  1 root    root    16 2011-10-10 21:13 .created_by_python-fstab
drwxr-x---  1 mslundy users 4096 2011-11-07 15:30 NTFS Data


here's fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda7 :
UUID=3aa8a07d-d2d5-4779-8a8e-7f17ff37783e	/	ext4	defaults	0	1

#Entry for /dev/sda5 mounts the shared NTFS Data partition:
UUID=A04A69F04A69C41E	/media/NTFS\040Data	ntfs-3g	auto,users,uid=1000,gid=100,dmask=027,fmask=137,UTF-8	0	0

#Entry for /dev/sda6 :
UUID=d6d254c0-fc97-4a07-b03e-8d4d114505a9	/swap	swap	sw	0	0

#The following lines hide Windows system partitions from non-priviledged Ubuntu users:
/dev/sda1 /Windows/sda1 ntfs defaults,noauto,umask=777 0 0
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
/dev/sda3 /Windows/sda3 ntfs defaults,noauto,umask=777 0 0

---

### Post by mcduck on 2011-11-09
Based on that I'd assume the problem is with the fstab line. I'm not familiar with the mount options for ntfs-3g so you'll have to check them yourself.

Perhaps you could try also creating a mount point with no spaces in the name, and setting the fstab to mount the drive there? Having a different mount point in fstab than what the automount system will use (the label of the partition) would help when trying to figure out which mechanism is actually mounting the drive... If the automount mechanism is the one doing the mounting, that's a sign that the fstab line is wrong.

(also you can probably safely remove the ".created_by_python-fstab"-file from /media)

---

### Post by RMOP on 2011-11-09
Well, I think I've solved it. I won't so mark the thread until after a reboot.

With the line commented out here the initial output:

~$ ls -la /media
total 16
drwxr-xr-x  3 root root 4096 2011-11-09 17:24 .
drwxr-xr-x 26 root root 4096 2011-11-07 23:28 ..
-rw-r--r--  1 root root   16 2011-10-10 21:13 .created_by_python-fstab
drwxr-xr-x  2 root root 4096 2011-11-04 20:41 NTFS Data



Navigating to /media in nautilus shows NTFS Data to be an empty DIRECTORY. After manually mounting "NTFS Data" from "Places" a drive icon with the same name appeared in /media. I then removed the empty directory of the same name using the command line. Got rid of the file as well. Now things appear to be as they should be. Before a reboot, that is.

After unmounting NTFS Data, but before deleting the text file, output is:

/media$ ls -la /media
total 12
drwxr-xr-x  2 root root 4096 2011-11-09 17:48 .
drwxr-xr-x 26 root root 4096 2011-11-07 23:28 ..
-rw-r--r--  1 root root   16 2011-10-10 21:13 .created_by_python-fstab

With the partition remounted (and file deleted):

/media$ ls -la /media
total 12
drwxr-xr-x  3 root    root    4096 2011-11-09 17:50 .
drwxr-xr-x 26 root    root    4096 2011-11-07 23:28 ..
drwx------  1 mslundy mslundy 4096 2011-11-07 15:30 NTFS Data

I'll reboot now and get back.

---

### Post by Morbius1 on 2011-11-09
Assuming you want to have this automount at boot there is a very old bug that might be the culprit so try this:

[1] Unmount the partition:
```
sudo umount "/media/NTFS Data"
```[2] Change the line in fstab from UUID=xxxxx to /dev/disk/by-uuid/xxxxx:
```
/dev/disk/by-uuid/A04A69F04A69C41E /media/NTFS\040Data ntfs-3g auto,users,uid=1000,gid=100,dmask=027,fmask=137,UTF-8    0    0
```[3] Then run the following command to test for errors and mount the partition with the new line in fstab ( it also saves you a reboot ) :
```
sudo mount -a
```Should that not work do it by label:
```
/dev/disk/by-label/NTFS\040Data /media/NTFS\040Data ntfs-3g auto,users,uid=1000,gid=100,dmask=027,fmask=137,UTF-8    0    0
```By the way "users" won't do what you think it will do and "gid=100" won't work unless you added users to the gid=100 group. But it won't do any harm to have it there.

---

### Post by RMOP on 2011-11-09
Well, many thanks for your interest and patience. I KNOW I'm in way over my head. I usually am w Ubuntu but have always gotten by by trolling the forums and looking for things that have worked, copying them, and modifying as needed.

All this started because I needed my drive to automount so FireFox could read its profile on that partition.

Your first suggestion, /dev/disk/by-uuid seems to have worked, with a few caveats.

The partition mounts on boot. I can unmount it from "Places" but can not subsequently re-mount it, either from "Places" or a Nautilus window. Command line sudo is required. I've still got something wrong. But this is as close as I've come. And YES, the "Phantom NTFS Data" remains ABSENT from "Places."

What might be in order to beable to unmount and re-mount as a user?

Again, thanks.

---

### Post by Morbius1 on 2011-11-09
> The partition mounts on boot. I can unmount it from "Places" but can not  subsequently re-mount it, either from "Places" or a Nautilus window.This question comes up from time to time and I'll be honest and admit I just don't understand it. The whole point of adding something to fstab is so that it mounts automatically at boot with ( in the case of an ntfs partition ) the ownership and permissions you want it to have. Why add the "users" option to allow anyone to unmount it? Sounds like chaos to me :)

Get rid of the "users" option so that only root can unmount the partition and only root can remount the partition. With your line in fstab it will mount with:
owner = you
group = users
directory permissions = 750
file permissions = 640

Assuming you actually have anyone in the "gid=100" group then you have full access and everyone else has only read access.

---

### Post by RMOP on 2011-11-09
Thanks again. I kept the user option because I'm the ONLY user and am lazy and don't always want to drop to the terminal. I'd really like to be do unmount and remount from the gui. Just preference.

BUT, I ADDED user initially as an experiment as I was having trouble when auto-mounting this drive. The whole reason I got started on this was because I couldn't start FireFox before this partition was mounted, as it stores the shared FF profile. It SEEMED simple to put a line in fstab to handle this, but I've been chasing rabbit trails for weeks. Your suggestions have brought me the closest to a satisfactory solution. I'll drop the user option and see what happens...

---

### Post by Morbius1 on 2011-11-09
The uid=1000 option made you the owner of the partition. "User" and "users" has nothing to do with ownership and in the case of "user" is irrelevant as an fstab option ( at least without the "noauto" option ) since the only user at the moment of mount in fstab is root.

There is no reason once fstab has mounted the partition to ever unmount it.

---

### Post by RMOP on 2011-11-09
I concede the point. Thanks for the guidance and insight. As the purpose for which I opened this thread has been addressed, I'll mark it solved.

---

