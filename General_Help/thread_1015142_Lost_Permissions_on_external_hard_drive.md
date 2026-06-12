---
title: "Lost Permissions on external hard drive"
date: 2008-12-18
forum: General Help
---

### Post by shelbyvision on 2008-12-18
This problem just cropped up today. I don't know if it relates to my other problem, posted here: [COLOR="Red"][http://ubuntuforums.org/showthread.php?t=1014824]("http://ubuntuforums.org/showthread.php?t=1014824")[/COLOR]. I have an external hard drive on which I store all of my files. Suddenly, The hard drive is designated as "read only". I never changed anything about it. This hard drive is called "WD USB 2", which is ubuntu's name for it. When I tried chmod in the terminal, it told me there was no such file or directory. Between this and the other problem, I can't do any of the tasks I was trying to do. Help, please!
Steve

---

### Post by xjcannonx on 2008-12-18
try posting the output of ```
sudo fdisk -l
df -h
```
and what does /var/log/messages say

---

### Post by shelbyvision on 2008-12-18
> **xjcannonx said:**
> try posting the output of ```
sudo fdisk -l
df -h
```

OK, I did that. Nothing about permissions there that I could recognize.

and what does /var/log/messages say

It's over 6000 lines, and I have no idea what to look for.
:confused:
Steve

---

### Post by taurus on 2008-12-18
Why not just post the outputs of those two commands from a terminal?

---

### Post by shelbyvision on 2008-12-18
> **taurus said:**
> Why not just post the outputs of those two commands from a terminal?

OK, here you are:

steve@localhost:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1096     8803588+   7  HPFS/NTFS
/dev/sda2            1097        2371    10241437+  83  Linux
/dev/sda3            2372        2434      506047+   5  Extended
/dev/sda5            2372        2434      506016   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   c  W95 FAT32 (LBA)
steve@localhost:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.7G  4.6G  4.6G  50% /
varrun                125M  224K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   96K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   34M   91M  28% /lib/modules/2.6.22-15-generic/volatile
/dev/sdb1              75G   29G   47G  38% /media/WD USB 2
steve@localhost:~$

---

### Post by taurus on 2008-12-18
Do you want to write to /dev/sdb1 (or /media/"WD USB 2")?

Try running these from a terminal.

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```
And when you are done with it, don't just unplug it from your computer.  You need to unmount it first before you unplug it.

```
sudo umount /media/sdb1
```

---

### Post by shelbyvision on 2008-12-18
> **taurus said:**
> Do you want to write to /dev/sdb1 (or /media/"WD USB 2")?

Try running these from a terminal.

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
ls -la /media/sdb1
```
And when you are done with it, don't just unplug it from your computer.  You need to unmount it first before you unplug it.

```
sudo umount /media/sdb1
```


Yes I want to write, delete files, change names of files. All of my important files are there.
I tried the code and got this:

steve@localhost:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not found
steve@localhost:~$ sudo mkdir /media/sdb1
steve@localhost:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
mount: special device /dev/sdb1 does not exist
steve@localhost:~$ ls -la /media/sdb1
total 8
drwxr-xr-x 2 root root 4096 2008-12-18 20:59 .
drwxr-xr-x 6 root root 4096 2008-12-18 20:59 ..
steve@localhost:~$

---

### Post by shelbyvision on 2008-12-20
I still need help with this. None of the advice I've gotten so far has helped. 
I did some experimenting and discovered this much: The external hard drive WORKS NORMALLY in Windows on two different computers, but NOT in Ubuntu on EITHER of those two computers, and they are not connected by network. What puzzles me is it has always worked normally in Ubuntu before, and now it doesn't. :confused:
Oh, I also found out that the correct location is /media/sdb1.

---

### Post by taurus on 2008-12-20
What are the outputs of these commands again?

```
dmesg | tail
sudo fdisk -l
df -h
```
I assume the drive is on and plugged in.

---

### Post by shelbyvision on 2008-12-20
> **taurus said:**
> What are the outputs of these commands again?

```
dmesg | tail
sudo fdisk -l
df -h
```
I assume the drive is on and plugged in.

Here's what it says:

steve@laptop:~$ dmesg | tail
[   90.356000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   90.356000]     File system has been set read-only
[   90.988000] FAT: Filesystem panic (dev sda1)
[   90.988000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  115.876000] FAT: Filesystem panic (dev sda1)
[  115.876000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  142.920000] FAT: Filesystem panic (dev sda1)
[  142.920000]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  147.736000] FAT: Filesystem panic (dev sda1)
[  147.736000]     fat_get_cluster: invalid cluster chain (i_pos 0)
steve@laptop:~$ sudo fdisk -l
[sudo] password for steve:

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab07ab07

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           3       24066   a0  IBM Thinkpad hibernation
/dev/hda2   *           4        1915    15358140    7  HPFS/NTFS
/dev/hda3            1916        4736    22659682+  83  Linux
/dev/hda4            4737        4864     1028160    5  Extended
/dev/hda5            4737        4864     1028128+  82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9728    78140128+   c  W95 FAT32 (LBA)
steve@laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              22G  6.2G   15G  31% /
varrun                252M  220K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   72K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-15-generic/volatile
/dev/sda1              75G   28G   47G  38% /media/WD USB 2
steve@laptop:~$

---

### Post by taurus on 2008-12-20
Maybe it's a good idea to connect that external drive to a windows machine and run defrag and scandisk of it.

And when you're done, use the Safely Remove Hardware to remove it; don't just unplug it.  Now, see if you have problem with it in Ubuntu.

---

### Post by shelbyvision on 2008-12-20
> **taurus said:**
> Maybe it's a good idea to connect that external drive to a windows machine and run defrag and scandisk of it.

And when you're done, use the Safely Remove Hardware to remove it; don't just unplug it.  Now, see if you have problem with it in Ubuntu.


OK, I tried that. Windows defrag won't go because the analysis gets stopped because of a file called .Trash-steve. since it's a Ubuntu-created file, I can't look at it in Windows, but I could delete it from there. I can't delete it in Ubuntu because of the permissions problem. Is it safe to delete that file?

---

### Post by taurus on 2008-12-20
It's just a trash bin so it's safe to remove it.

---

### Post by shelbyvision on 2008-12-20
> **taurus said:**
> It's just a trash bin so it's safe to remove it.


Well, that won't work, either. Windows says it can't delete it because it's corrupted and unreadable.

---

### Post by shelbyvision on 2008-12-20
Is this problem unsolvable? It seems to me that if it works correctly in Windows, but not in Ubuntu, it can't be a hardware problem.

---

### Post by shelbyvision on 2008-12-20
More info: 
1. In Ubuntu, the file .Trash-steve is described as "unknown" and if I check its properties, everything about it is listed as "unknown".
2. I can't access the files at all from the terminal. If I try, here's what I get:
steve@laptop:/media$ cd /media/sdb1
steve@laptop:/media/sdb1$ ls
steve@laptop:/media/sdb1$ sudo ls
steve@laptop:/media/sdb1$

---

### Post by taurus on 2008-12-20
Try listing the . (hidden) files/directories too.

```
sudo ls -la
```

---

### Post by shelbyvision on 2008-12-20
> **taurus said:**
> Try listing the . (hidden) files/directories too.

```
sudo ls -la
```


OK, here are the results of that:

steve@laptop:/media/sdb1$ sudo ls -la
[sudo] password for steve:
total 8
drwxrwxr-x 2 root root 4096 2008-12-19 22:25 .
drwxr-xr-x 6 root root 4096 2008-12-20 16:01 ..
steve@laptop:/media/sdb1$

---

### Post by shelbyvision on 2008-12-20
I did a little reading on commands and tried some other things. I'm not sure what to make of this. It seems to shows sdb1 as subset of sdb1, and WD USB 2 as another subset, and the year, 1969, which, of course is impossible!

steve@laptop:/media/sdb1$ ls -la .. -l
total 56
drwxr-xr-x  6 root  root  4096 2008-12-20 20:48 .
drwxr-xr-x 21 root  root  4096 2008-09-26 17:44 ..
lrwxrwxrwx  1 root  root     6 2008-09-25 06:54 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2008-09-25 06:54 cdrom0
lrwxrwxrwx  1 root  root     7 2008-09-25 06:54 floppy -> floppy0
drwxr-xr-x  2 root  root  4096 2008-09-25 06:54 floppy0
-rw-r--r--  1 root  root   104 2008-12-20 20:48 .hal-mtab
-rw-------  1 root  root     0 2008-12-20 20:48 .hal-mtab-lock
drwxrwxr-x  2 root  root  4096 2008-12-19 22:25 sdb1
drwx------ 14 steve root 32768 1969-12-31 19:00 WD USB 2
steve@laptop:/media/sdb1$

---

### Post by taurus on 2008-12-20
```
ls -la /media/sdb1/"WD USB 2"
```

---

### Post by shelbyvision on 2008-12-20
> **taurus said:**
> ```
ls -la /media/sdb1/"WD USB 2"
```


Now we may getting somewhere! The Quotation marks are magic. That code didn't work but I tried /media/"WD USB 2", and got this: 

steve@laptop:~$ ls -la /media/"WD USB 2"
total 676
drwx------ 14 steve root 32768 1969-12-31 19:00 .
drwxr-xr-x  6 root  root  4096 2008-12-20 20:48 ..
-rwx------  1 steve root   565 2006-12-18 22:03 30's-40's music.lnk
drwx------  2 steve root 32768 2003-01-31 14:25 autorun
-rwx------  1 steve root    36 2002-10-17 10:56 autorun.inf
-rwx------  1 steve root 42386 2008-09-27 21:58 avem2.mid
drwx------  4 steve root 32768 2008-03-03 22:58 Betsy Backup
-rwx------  1 steve root   502 2008-05-06 13:57 Business-Urn.lnk
-rwx------  1 steve root  6148 2006-01-09 11:35 .DS_Store
drwx------  6 steve root 32768 2008-08-03 10:53 Fonts
drwx------  2 steve root 32768 2008-06-18 23:52 forauntcarol
drwx------ 10 steve root 32768 2008-03-28 18:39 HPbkup3-08
drwx------  2 steve root 32768 2008-07-13 14:20 Local Folders
?---------  ? ?     ?        ?                ? /media/WD USB 2/.Trash-steve
drwx------  2 steve root 32768 2005-10-16 22:41 Recycled
-rwx------  1 steve root   519 2008-05-06 09:20 Shortcut to My Pictures.lnk
-rwx------  1 steve root   610 2007-02-24 07:19 Shortcut to PovScn.lnk
drwx------ 18 steve root 32768 2008-12-02 22:03 Steves Notebook
drwx------  3 steve root 32768 2005-10-16 13:38 System Volume Information
drwx------  2 steve root 32768 2006-01-09 11:16 .Trashes
drwx------  6 steve root 32768 2008-12-06 07:14 Ubuntu_Backup
-rwx------  1 steve root   689 2008-04-25 19:06 urn pictures.lnk
steve@laptop:~$ 

Now, how do i delete that .Trash-steve file?

---

### Post by shelbyvision on 2008-12-20
I tried removing .Trash-steve in the prescribed way, and here's what happened:

steve@laptop:~$ sudo rm  /media/"WD USB 2"/.Trash-steve
[sudo] password for steve:
rm: cannot remove `/media/WD USB 2/.Trash-steve': Input/output error
steve@laptop:~$

---

### Post by shelbyvision on 2008-12-21
I tried chmod, with no luck, but I'm very inexperienced at this, so I might have done something wrong. Here's what happened:

steve@laptop:/media/WD USB 2$ sudo chmod 775 /media/"WD USB 2"
chmod: changing permissions of `/media/WD USB 2': Read-only file system
steve@laptop:/media/WD USB 2$

---

### Post by shelbyvision on 2008-12-21
I found this on an older thread by Beefeater, [http://ubuntuforums.org/member.php?u=157537]("http://ubuntuforums.org/member.php?u=157537"),who had a very similar problem. I don't understand the code, but I thought maybe one of you experts could explain it to me, and tell me how I might apply it in my specific situation.

Quote:

Hi,

I solved this 7-8 months ago and haven't had any problems since.

Create a executable file for example /usb/bin/usbhdfix and place the following in it.

Code:

#!/bin/bash
echo 1024 > /sys/block/$1/device/max_sectors
echo 1 > /sys/block/$1/device/scsi_disk:*/allow_restart

1024 works for me but I've also heard about people going lower than default with good results.
I have a Seagate FreeAgent which also have the problem with restarting after spinning down so solution for that is added as well.

Then create a udev-rule.

Code:

# /etc/udev/rules.d/50-fix_usb_hd.rules
SUBSYSTEMS=="scsi", ATTRS{vendor}=="Seagate", ATTRS{model}=="FreeAgentDesktop", RUN+="/usr/bin/usbhdfix %k"

---

### Post by shelbyvision on 2008-12-22
I really want to fix this. 
I read about the /etc/fstab file, and I looked at it, and the external hard drive is not listed there.
I'm wondering if adding a line there would solve this problem, but I'm not experienced enough to know how it should go. can someone help me with this?

---

