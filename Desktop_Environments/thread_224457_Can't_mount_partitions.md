---
title: "Can't mount partitions"
date: 2006-07-28
forum: Desktop Environments
---

### Post by m.musashi on 2006-07-28
This has been an on going problem since I upgraded to dapper. I have 2 HDs (one SATA and one IDE). Both have a couple partitions. In breezy I was able to use the diskmounter app to mount all partitions and have them be accessible each time I logged on.

My understading is that dapper automated the process and you no longer need to use diskmounter or manually edit anything. This seems to be the case on both laptops on which I have installed dapper. However, I have not had the same luck on my desktop. While the drives are visible, when I try and open any of them I get a message saying "unable to mount the selected volume." Further information is given:
```
error: device /dev/sda1 is not removable

error: could not execute pmount
```
I thought maybe a clean install would solve the problem and I just did that. However, the same problem exists.

Any ideas on how I can solve this problem?
Thanks.

---

### Post by mlind on 2006-07-28
Is /dev/sda1 a removable drive? I'm not sure how pmount works, but you might find it's manualy page very helpful, at least POLICY section.

---

### Post by m.musashi on 2006-07-28
Thanks for the reply. /dev/sda1 is actually the root partition drive. It is the partition with windows (/dev/sda2 is ubuntu). So, no, it's not a removable drive. Interestingly enough, if I plug in a USB drive it mounts without any problems.

I don't know what pmount is either. I didn't specifically run pmount. I only double clicked the drive partition I wanted to view (in this case the windows partition but I get the same error with other partitions). For example, if I try and open the fat32 partition on my second hard drive I get this error:
```
Unable to mount the selected volume
error: device /dev/hdc1 is not removable

error: could not execute pmount
```
Any ideas would be greatly appreciated. With Dapper I am approaching 100% ubuntu but not being able to access other partitions is kind of buzz kill. Thanks in advance.

---

### Post by m.musashi on 2006-08-01
If anyone has any ideas, I could still use some help with this.

I went ahead and tried using "diskmounter". It said all the partitions where now mounted but I get the same error as before. It also woked fine in breezy but after moving to dapper it's one of the few things that doesn't.

Thanks in advance.

---

### Post by aysiu on 2006-08-01
Manually editing something might help you. I know you think it's supposedly not necessary in Dapper, but it is.
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by m.musashi on 2006-08-01
Thanks for the links. I'm not that versed in Linux yet to manually edit stuff without some directions. I hadn't been able to find anything so that is actually exactly what I was looking for. Thanks.

However, it seems the diskmounter script actually worked. It didn't add them to the window that opens when you click places -> computer so that is why I thought it didn't work (it actually removed the icons that were there) but it did add them to /media. However, my Suse partition still shows up in this window and it still fails to mount. I'll go play with the links you provided.

As for being automatic in Dapper, that was an assumption based on the fact that partitions were automatically mounted after installing Dapper on two laptops (only one drive in each case but two or more partitions). Given that, I can't understand why it hasn't been working on my desktop. The drives actually show (i.e. there is a drive icon) up but can't be accessed.

---

### Post by dizm on 2006-08-01
can you post the output of (as root):
 cat /etc/fstab
 mount
 fdisk -l

to learn, look in the corresponding man pages:
 man fstab
 man mount
 man fdisk

---

### Post by m.musashi on 2006-08-01
Sure. I've been playing with this a bit so it's not quite the same as before.

```
jim@number6:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#Added by diskmounter utility
/dev/sda1 /media/windows ntfs nls=utf8,umask=0222 0 0
#Added by diskmounter utility
/dev/hdc1 /media/files vfat iocharset=utf8,umask=000 0 0
```

```
jim@number6:~$ mount
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/sda1 on /media/windows type ntfs (ro,noexec,nosuid,nodev,fmask=0111,dmask=0000)
/dev/hdc1 on /media/files type vfat (rw,iocharset=utf8,umask=000)

```

fdisk -l didn't produce any output.

---

### Post by m.musashi on 2006-08-01
Oops. Didn't run as root. Here it is.
```
jim@number6:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12498   100390153+   7  HPFS/NTFS
/dev/sda2           12499       23967    92124742+  83  Linux
/dev/sda3           23968       24321     2843505    5  Extended
/dev/sda5           23968       24321     2843473+  82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4943    39704616    c  W95 FAT32 (LBA)
/dev/hdc2            4944        9729    38443545    f  W95 Ext'd (LBA)
/dev/hdc5            4944        5125     1461883+  82  Linux swap / Solaris
/dev/hdc6            5126        6975    14860093+  83  Linux
/dev/hdc7            6976        9729    22121473+  83  Linux

```

---

### Post by m.musashi on 2006-08-01
Okay, one more thing. While I seem to have the the ntfs and fat32 partitions mounting, I still get icons for two linux partitions (from suse) but they are not accessible. They are not in the fstab file at all but still show up (see attached image).

Also, although I edited /etc/fstab to have the fat32 mount to /media/files it shows up as DSK2_VOL1. Any idea what's up with that?

---

### Post by dizm on 2006-08-02
if the problem is that you can't mount hdc6 and hdc7, you should be able to fix that by adding corresponding lines to /etc/fstab, something like:
  /dev/hdc6 /media/xyz ext3 defaults  0  0
then issue: mount /dev/hdc6
it's worth experimenting with options, so you can mount them without being root, or so they mount automagically at boot time

if the problem is that you can't mount them by clicking on the icon, then i suggest you repost with a different title.  That browser seems to think the partitions are on media (pmount is for removable media).  i can't help with that (i use kde, precisely because i've had problems like this with gnome).

good luck!

---

### Post by m.musashi on 2006-08-03
Thanks for the help. I have managed to edit /etc/fstab to get all the partitions I want mounted to mount. However, there are still two small problems and maybe, as you suggest, I should post as a new topic.

In short, in case someone reads through this and knows the answer, the root partition for my suse install continues to show up in the nautilus browser but is not accessible (refer to screenshot in my previous post). Actually, I don't want that partition to mount or show up. It is there even though there is no entry for it in /etc/fstab or anywhere else that I can see.

The other problem is that my shared partition mounts as DSK2_VOL1. All the other partitions seems to use a name scheme that includes the name of the /media folder where they around mounted. This is the only one that does not follow that scheme. It's not a huge issue but it's frustrating to not understand why or make it do what I want.

Thanks.

---

