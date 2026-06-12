---
title: "Software RAID question"
date: 2006-09-26
forum: Desktop Environments
---

### Post by SgtPepperKSU on 2006-09-26
This seems like a simple problem, so it has probably been answered before; I couldn't find it, though.  If that's the case, please point me to one such place.

I have been a casual linux user for several years now and am finally ready to give windows the heave-ho on one of my boxes.  However, this is my first attempt at software raid.  I would like to use the disk that windows used to be on as a mirror of a partition on my main ubuntu drive.

Here is what I have (am posting from work, so I don't have the numbers in front of me: sizes are approximate):

/dev/hda = 120 GB drive
/dev/hda1 = 75 GiB partition (/)
/dev/hda3 = 37.25 GiB partition (want to be mirrored)
/dev/hda5 = 785 MiB partition (swap)
/dev/hdb = 40 GB drive
/dev/hdb1 = 37.25 GiB partition (want to be mirror)

Here is the command I try:
```
sudo mdadm --create /dev/md0 --verbose --level raid1 --raid-devices=2 /dev/hda3 /dev/hdb1
```
I get a response that it cannot open hda3 or hdb1 because they are busy or in use.  I have tried running this command from the live cd with the same result.

Is this even something I can do?  If so, what am I doing wrong?

Thanks in advance!

---

### Post by whizbaby on 2006-09-26
Not knowing much about mdadm (don't have the time to read a 974 line manual now) I guess that you will have to unmount the drives before doing that. A RAID in home use mostly is only one device to your filesystem, perhaps mdadm will mount the drives in a special way or create a device (maybe this /dev/md0-thing) you can mount instead of the two HDs (hoping to be a little helpful).

---

### Post by SgtPepperKSU on 2006-09-26
Unmounting / is not possible in normal operation (right?), but I made sure they weren't mounted when I tried it with the live cd.

---

### Post by whizbaby on 2006-09-26
Sure? How can an unmounted drive be 'busy' (strange...)? And why unmounting /, you didn't say it *wants to be mirrored*. You could try to soft-mirror by scripting (it's a one-liner using rsync) and use of cron.
Let's say you want to synchronise hypothetical mount points media/backup1 and /media/backup2 (contents of backup1 go to backup2):
rsync -azvxb /media/backup1/ /media/backup2
(first slash after backup1 is important)
In terminal (to test it) you will have to type a sudo before it. See *man rsync* for details and additional options. You can type the above line in an editor (after typing this line:
#!/bin/bash
to make it a script) and save it. Make it executable with **chmod u+x *replace_by_name_of_script_you_saved***. For cron see this
[http://doc.gwos.org/index.php/Crontab](http://doc.gwos.org/index.php/Crontab)
EDIT:
here a copy-and-paste (maybe I talk a little confusing)
#!/bin/bash
rsync -azvxb /media/backup1/ /media/backup2

---

### Post by SgtPepperKSU on 2006-09-26
Yes, I'm sure.  That's why I came here; I don't know why the disks are busy, so I couldn't get past that error.  Is there a way to find out what's making them "busy"?  I mentioned unmounting / because it is on the same disk as the partition I want to mirror, and I made sure there were no partitions on either disk mounted.

Your rsync suggestion would work, but I'm still wondering why I can't set up the RAID.  If I can't at least find out *why* it won't work, it will continue to haunt me ;-).  Any more guidance would be greatly appreciated.

---

### Post by whizbaby on 2006-09-26
I found this on my computer (seems rather good), should be on yours,too (installs with mdadm).
file:///usr/share/doc/mdadm/rootraiddoc.97.html
(since ubuntu is built on debian it will be the same on this level)
You need raid compiled into your kernel if you want to boot from the disk the raid is on (not default).

---

### Post by whizbaby on 2006-09-26
Oh, and I don't know if you can build a raid on existing data as easy as that, in the howto md0 is formatted after creation and the data is copied to it later.(BTW don't *move* data, copy it and remove the source for safety)

---

### Post by SgtPepperKSU on 2006-09-26
Thanks! I'll take a look.  I saw several references to needing it in the kernel to boot off of raid, but I didn't think it applied to me since I'm not booting off of the raid - just the same disk as the raid.  I'll take a look, though.

Oh, the partition I want mirrored is completely empty right now.  I just created it for this purpose (that's why it's the same size as the entire other disk).  So, data loss is not a concern.

Thanks again.  I'll report back when I get a chance to try it.

---

### Post by whizbaby on 2006-09-26
Now I think what you first thought is right, I may have misunderstood the howto. (I thought *boot from RAID device* would mean the disk...](*,) )
Anyway, the howto is quite interesting.

---

### Post by SgtPepperKSU on 2006-09-27
A little more info now that I'm at home:
```
[FONT="Courier New"]**:~$ sudo mdadm --verbose --create /dev/md0 --level raid1 --raid-devices=2 /dev/hda3 /dev/hdb1**
mdadm: Cannot open /dev/hda3: Device or resource busy
mdadm: Cannot open /dev/hdb1: Device or resource busy
mdadm: create aborted
**:~$ sudo fdisk -l /dev/hdb**

Disk /dev/hdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4863    39062016   fd  Linux raid autodetect
**:~$ sudo fdisk -l /dev/hda**

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9637    77409171   83  Linux
/dev/hda2           14501       14593      747022+   5  Extended
/dev/hda3            9638       14500    39062047+  fd  Linux raid autodetect
/dev/hda5           14501       14593      746991   82  Linux swap / Solaris

Partition table entries are not in disk order
**:~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
**:~$ cat /etc/mtab**
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-27-686/volatile tmpfs rw 0 0
**:~$ sudo /usr/sbin/lsof /dev/hdb1**
**:~$ sudo /usr/sbin/lsof /dev/hda3**
**:~$ sudo /usr/sbin/lsof /dev/md0**
**:~$ sudo /usr/sbin/lsof | grep hdb1**
**:~$ sudo /usr/sbin/lsof | grep hda3**
**:~$ sudo /usr/sbin/lsof | grep md0**
md0_raid1  2054       root  cwd       DIR        3,1    4096          2 /
md0_raid1  2054       root  rtd       DIR        3,1    4096          2 /
md0_raid1  2054       root  txt   unknown                               /proc/2054/exe
**:~$ sudo /usr/sbin/lsof | grep md1**
md1_raid1  3734       root  cwd       DIR        3,1    4096          2 /
md1_raid1  3734       root  rtd       DIR        3,1    4096          2 /
md1_raid1  3734       root  txt   unknown                               /proc/3734/exe
**:~$ sudo /usr/sbin/lsof | grep md2**
**:~$ cat /etc/raidtab**
cat: /etc/raidtab: No such file or directory
**:~$ cat /proc/mdstat**
Personalities : [raid1]
md1 : active raid1 dm-3[1] dm-2[0]
      39061952 blocks [2/2] [UU]

md0 : active raid1 hda3[0] hdb1[1]
      39061952 blocks [2/2] [UU]

unused devices: <none>
**:~$ sudo mdadm --verbose --create /dev/md0 --level raid1 --raid-devices=2 /dev/hda3 /dev/hdb1**
mdadm: Cannot open /dev/hda3: Device or resource busy
mdadm: Cannot open /dev/hdb1: Device or resource busy
mdadm: create aborted
**:~$**[/FONT]
```

---

### Post by SgtPepperKSU on 2006-09-27
I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=129498") and got it working.  For some reason, mdadm had automagically created a raid array for me already without creating a raidtab. I just had to stop it first.  Then, I was able to create my array.  So, all I had to do was:
```
[FONT="Courier New"][B]:~$ sudo mdadm --stop /dev/md0
:~$ sudo mdadm --stop /dev/md1
:~$ sudo mdadm --verbose --create /dev/md0 --level raid1 --raid-devices=2 /dev/hda3 /dev/hdb1[/B]
mdadm: /dev/hda3 appears to be part of a raid array:
    level=1 devices=2 ctime=Mon Sep 25 15:20:38 2006
mdadm: /dev/hdb1 appears to be part of a raid array:
    level=1 devices=2 ctime=Mon Sep 25 15:20:38 2006
mdadm: size set to 39061952K
Continue creating array? y
mdadm: array /dev/md0 started.
**:~$ cat /proc/mdstat**
Personalities : [raid1]
md0 : active raid1 hdb1[1] hda3[0]
      39061952 blocks [2/2] [UU]
      [>....................]  resync =  1.4% (572544/39061952) finish=29.1min speed=22020K/sec

unused devices: <none>[/FONT]
```

Thanks for your help!

---

