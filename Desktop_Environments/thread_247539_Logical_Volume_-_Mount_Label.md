---
title: "Logical Volume - Mount Label"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Aikon- on 2006-08-30
UPDATE:

I realized I places this under the wrong forum, so I've moved it to this thread:
[http://www.ubuntuforums.org/showthread.php?t=247645](http://www.ubuntuforums.org/showthread.php?t=247645)

---

### Post by Aikon- on 2006-08-30
Help!

Okay, this is a little more serious than the previous problem.

When I mount the logical volume lvdata as I indicated above, its getting mounted in read-only mode.. I cannot write to this volume!



Output of vgdisplay:
```
  --- Volume group ---
  VG Name               lvga
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               298.09 GB
  PE Size               4.00 MB
  Total PE              76311
  Alloc PE / Size       76311 / 298.09 GB
  Free  PE / Size       0 / 0
  VG UUID               qqcsh2-BJ7p-1h2M-zp9J-Caq1-IZKL-GF3msO

```

Output of lvdisplay:
```
  --- Logical volume ---
  LV Name                /dev/lvga/lvhome
  VG Name                lvga
  LV UUID                yGT7Vm-2qdK-Nz1w-emCf-RZJk-lrvm-W5G1eC
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                50.00 GB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0

  --- Logical volume ---
  LV Name                /dev/lvga/lvdata
  VG Name                lvga
  LV UUID                Yqn53K-Ruk1-WE4z-3x3e-2hAg-rgMy-5OTViQ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                248.09 GB
  Current LE             63511
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1

```

Output of   ls -l /media:
```
total 44
lrwxrwxrwx 1 root root        6 2006-07-26 14:21 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2006-07-26 14:21 cdrom0
drwxr-xr-x 2 root root     4096 2006-08-30 06:56 cdrom-1
drwxr-xr-x 2 root root     4096 2006-08-30 06:56 dvdrecorder
drwxrwxrwx 2 root root     4096 2006-08-30 18:26 file-03
dr-xr-x--- 1 root plugdev 12288 2006-08-30 07:03 pet-file-02
dr-xr-x--- 1 root plugdev 16384 2006-08-30 07:03 pet-win-01

```


My /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/lvga/lvdata        /media/file-03  ext3    defaults,errors=remount-ro      0       1
/dev/sda1       /media/pet-file-02 ntfs defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/pet-win-01 ntfs  defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by mssever on 2006-08-30
> **Aikon- said:**
> However, the icon on my desktop (and consequently the entry in "Places" reads "file-03", yet I want it to read "Asuka". This should be possible.. my windows system (which has a volume-label of "System" on an NTFS partition) shows up as System, my iPod shows up as "NIKKI" (this is the one exception to the naming rule, named for my cat) and the same for various other devices like USB keys, CD's, DVD's etc.

How can I make the volume show up as Asuka?
Try making a directory named Asuka and mounting to that.

As to your other problem, my idea is a bit of a stab in the dark as I've never used LVM (though it sounds really cool). I'm thinking that there's a error somewhere, and it gets mounted ro because of the errors=remount-ro in your fstab.
Try sudo ```
mount -o remount,rw /dev/lvga/lvdata
``` and see if that makes it writable. If so, you could change your fstab to remove the offending option (I've only seen that option on the root partition)--or, you could find and fix the problem, something I don't know much about.

---

### Post by Aikon- on 2006-08-30
Hmm.. nope, that didn't work...

If it means anything, I can write to /media/file-03 if I do something like
```
sudo nano /media/file-03/test.txt
```
note the sudo part =/

I guess this means that its actually being mounted in r/w, but that the permissions are incorrect.....

---

### Post by mssever on 2006-08-30
I don't know why I didn't think of this before, but typing [FONT=Courier New]mount[/FONT] will tell you how it's mounted. But I agree that it apears to be mounted rw.

Try ```
sudo chmod 777 /media/file-03
``` If that doesn't fix it, ```
sudo mkdir -p /media/file-03/test && sudo chmod 777 /media/file-03/test
touch /media/file-03/test/bogus.file
```

You could also try to chown the directory to your user, though I doubt that'll work.

---

### Post by Aikon- on 2006-08-30
> **mssever said:**
> I don't know why I didn't think of this before, but typing [FONT=Courier New]mount[/FONT] will tell you how it's mounted. But I agree that it apears to be mounted rw.

Try ```
sudo chmod 777 /media/file-03
``` If that doesn't fix it, ```
sudo mkdir -p /media/file-03/test && sudo chmod 777 /media/file-03/test
touch /media/file-03/test/bogus.file
```

You could also try to chown the directory to your user, though I doubt that'll work.

this is mount's output:
```
/dev/mapper/lvga-lvdata on /media/file-03 type ext3 (rw,noexec,nosuid,nodev,user=sarmitage)

```


gasp!

what did you do?!

```
sudo mkdir -p /media/file-03/test && sudo chmod 777 /media/file-03/test
touch /media/file-03/test/bogus.file
```

This created the directory, inside which I can write (i.e. create folders in Nautilus, or copy files etc.).

Any ideas on how to let me do it at /media/file-03 instead of /media/file-03/test level?

I've tried sudo chmod 777 /media/file-03

---

### Post by Aikon- on 2006-08-31
Umm..

Sitting in /media/file-03 in Nautilus, I could not create a folder.. but I could delete the folder /media/file-03/test that we created earlier, so I did. After hitting F5, the lost+found folder and the test.txt folder created from sudo earlier both got a little "lock" emblem, and now I can create folders/files in /media/file-03

I'm not exactly sure how you fixed it, but you did! or We did.. same thing ;)

Thanks alot for the help!

---

### Post by mssever on 2006-08-31
I'm glad it's fixed. I'll explain that code block for you--I think you can do a lot of this in Nautilus, but I'm more comfortable working from the command line.

mkdir means to create a directory. The -p means to create any additional directories up the tree that don't exist. It wasn't really necessary in this example.

chmod 777 means to give full permissions to a directory--or full permissions including the execute bit to regular files.

The && means to only do the second command (the chmod one) if the first one (mkdir) was successful.

Finally, touch means to update the last modified time of a file. If the file doesn't exist, touch tries to create it. This tells us if we're able to write to a directory.

---

### Post by Aikon- on 2006-08-31
> **mssever said:**
> I'm glad it's fixed. I'll explain that code block for you--I think you can do a lot of this in Nautilus, but I'm more comfortable working from the command line.

mkdir means to create a directory. The -p means to create any additional directories up the tree that don't exist. It wasn't really necessary in this example.

chmod 777 means to give full permissions to a directory--or full permissions including the execute bit to regular files.

The && means to only do the second command (the chmod one) if the first one (mkdir) was successful.

Finally, touch means to update the last modified time of a file. If the file doesn't exist, touch tries to create it. This tells us if we're able to write to a directory.


Heh, thank you :D  I knew what the majority of your commands were doing (with the exception of -p, &&, and touch), I was more referring to not knowing why doing that fixed the problem. But really, I wish more people on here would 'splain their commands, makes for much easier reading =)

Thanks again mate, now time for me to sleep... tomorrow: migrating /home off of / and onto the lvhome logical volume :-D

---

