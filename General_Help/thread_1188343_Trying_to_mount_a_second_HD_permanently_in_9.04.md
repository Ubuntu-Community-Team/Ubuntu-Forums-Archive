---
title: "Trying to mount a second HD permanently in 9.04"
date: 2009-06-15
forum: General Help
---

### Post by Cheule on 2009-06-15
Hi folks, it's been a long time since my last post :)

I've been a long-time 6.06 user, and recently I took the plunge and went for a fresh install of 9.04. What a treat! Much more automation, user-friendly etc.

I just have a couple of problems. During the install, two HD's were present in the system and recognised. However, booting to the desktop, the slave drive is not auto-mounted and when I do mount it myself, I can't write to it. I think I also need to format it properly.

Can anyone take me through this? I've tried adding a mount point in /etc/fstab but it never seems to have any effect no matter what I do?

Thanks in advance :)

---

### Post by michy99 on 2009-06-15
First, what are the outputs of```
sudo fdisk
cat /ect/fstab
```

---

### Post by Cheule on 2009-06-15
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=24191191-6923-455f-a2f5-acc5253bbb3e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f7fe2ecc-bc31-4af2-a3cb-605c07c1b675 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by michy99 on 2009-06-15
what about```
sudo fdisk -l
```

---

### Post by Cheule on 2009-06-15
Oops, sorry ](*,)


Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa978a978

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14384   115539448+  83  Linux
/dev/sda2           14385       14946     4514265    5  Extended
/dev/sda5           14385       14946     4514233+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008cec2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

---

### Post by michy99 on 2009-06-15
First thing is make a mount point.```
sudo mkdir /media/disk
```You can change the word 'disk' to whatever you want to call that disk. Then tell me what the output of this is:```
ls -ld /media/disk
```If you used a different name than 'disk' then use that instead.

---

### Post by Cheule on 2009-06-15
Thanks for the help so far! :)

I went with sdb as that is what it is :)

Here's the output:

```
drwxr-xr-x 2 root root 4096 2009-06-15 21:49 /media/sdb
```

If I read that right, I think only root has read/write access?

---

### Post by michy99 on 2009-06-15
> **Cheule said:**
> Thanks for the help so far! :)

I went with sdb as that is what it is :)

Here's the output:

```
drwxr-xr-x 2 root root 4096 2009-06-15 21:49 /media/sdb
```

If I read that right, I think only root has read/write access?

Yes, but we're going to change that.```
sudo chown USERNAME:users /media/sdb
```
Put your username where it says USERNAME. Then do ```
ls -ld /media/sdb
``` to check it.

---

### Post by Cheule on 2009-06-15
It now says:

```
drwxr-xr-x 2 cheule users 4096 2009-06-15 21:49 /media/sdb

```

---

### Post by michy99 on 2009-06-15
Okay, now we put a line into fstab to mount the drive automatically. Open fstab with```
gksudo gedit /etc/fstab
```Then add this line:```
/dev/sdb1 /media/sdb  ext3    relatime        0       2
```Save the file and exit. See if the drive mounts when you enter```
sudo mount -a
```If it works, it should automatically mount every time you boot.

---

### Post by Cheule on 2009-06-15
Right, two problems thus far.

1) It mounts ok on boot, however the drive is always shown on the desktop;
2) No write privelidges for me. "Create folder" is ghosted out for example.

Would formatting the second drive help?

---

### Post by michy99 on 2009-06-15
> **Cheule said:**
> Right, two problems thus far.

1) It mounts ok on boot, however the drive is always shown on the desktop;
2) No write privelidges for me. "Create folder" is ghosted out for example.

Would formatting the second drive help?

Is there anything already on the drive?

If you don't want the drive on the desktop, you can have it mount to /mnt instead of /media. Just do the same things but put /mnt in place of /media including in the fstab file.

I'm not sure what the problem is on permissions. What is the output of ```
ls -l /media/sdb1
``` (assuming it is still mounted under /media)

---

### Post by Cheule on 2009-06-15
```
total 0

```

---

### Post by procras on 2009-06-15
Typo alert.

Shouldnt that be

$ ls -l /media/sdb

Remember /dev/sdb1 is the partition and /media/sdb is the mount point.

You may or may not need to format it. The output of fdisk said that the 1 partition on on the disk is set to type 83 Linux.

When you mounted it with sudo mount -a you may have seen some info about what was in the partition by looking at 
$ tail -f /var/log/syslog

If it says that there is no filesysten on it you may need to unmount it and use mke3fs or some such to set it up as ext3 etc. before you mount it.

---

### Post by michy99 on 2009-06-15
So I assume there is nothing on the disk, but it is formated as a ext3, correct? I don't think reformating will change anything, but if the disk is empty, it won't hurt anything to try. Do you still get the same result from```
ls -ld /media/sdb
```

---

### Post by Cheule on 2009-06-16
The new command reports:

```
drwxr-xr-x 2 cheule users 4096 2009-06-15 21:49 /media/sdb
```

---

### Post by Cheule on 2009-06-16
> **michy99 said:**
> So I assume there is nothing on the disk, but it is formated as a ext3, correct?

Sorry - I left that bit out. The slave device was the primary device in the old system - it had Ubuntu 6.06LTS on it in the ext3 format. I had assumed that the partitioning service had found the drive and formatted it but obviously now not the case.

---

### Post by Cheule on 2009-06-17
> **michy99 said:**
> Yes, but we're going to change that.```
sudo chown USERNAME:users /media/sdb
```
Put your username where it says USERNAME. Then do ```
ls -ld /media/sdb
``` to check it.

I've took another stab at this and found that if I run the CHOWN command using cheule:cheule rather than cheule:users, I now am able to create directories and copy files over to it.

The only thing left is, although the drive has now been formatted to ext3 with GParted, there's a leftover folder on the drive called Lost+Found which is owned by root.

---

