---
title: "making my windows partition read/write"
date: 2005-12-04
forum: Desktop Environments
---

### Post by tazzik on 2005-12-04
Hi,
I got my windows partition (FAT32) /dev/hda1 to work using the ubuntu guide, however the owner is set to root and I cannot change it. Also some files are not opening as read-write, just read-only
please help
tazzik

---

### Post by flopsy on 2005-12-04
I think (though I'm not sure) that you need to modify your mount options. Replace /mnt/windows with your mount point in what follows.
```

e.g.
/dev/hda1        /mnt/windows         vfat              rw,user,noauto,uid=1000,gid=1000,umask=755        0             0

``` You may need different values for uid and gid. You want the first two values from the id command.

Also, do sudo chown `id -un`:`id -gn` /mnt/windows.

---

### Post by tazzik on 2005-12-04
it says 
chown: changing ownership of `/media/windows': Operation not permitted
help???

---

### Post by schdefan on 2005-12-04
you cannot change fat32 partition rights in ubuntu which dos not mean that you don't have read/write access. depends on how you mount it!

schdefan

---

### Post by aysiu on 2005-12-04
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by tazzik on 2005-12-04
i have done this guide but it still doesnt work
might i need to change the umask???

---

### Post by aysiu on 2005-12-04
[QUOTE=tazzik]i have done this guide but it still doesnt work
might i need to change the umask???[/QUOTE] You have done this guide? Can you post the output of these commands so I can see how you've done it? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by flopsy on 2005-12-04
Mount the drive and paste the results of
```
ls -l /media/windows
```

Then unmount the drive and paste the results of
```
ls -ld /media/windows
```

---

### Post by tazzik on 2005-12-04
to aysiu:
(sudo fdisk -l)```

Disk /dev/hda: 12.0 GB, 12072517632 bytes
255 heads, 63 sectors/track, 1467 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         510     4096543+   b  W95 FAT32
/dev/hda2             511        1467     7687102+   f  W95 Ext'd (LBA)
/dev/hda5             511         583      586341   82  Linux swap / Solaris
/dev/hda6             584        1467     7100698+  83  Linux

```
THEN.
(df -h)```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda6             6.7G  3.2G  3.2G  50% /
tmpfs                  94M     0   94M   0% /dev/shm
tmpfs                  94M   13M   82M  14% /lib/modules/2.6.12-10-386/volatile
/dev/hda1             3.9G  1.5G  2.5G  39% /media/hda1
/dev/sda2             3.8G  164M  3.7G   5% /media/ipod
/dev/hda1             3.9G  1.5G  2.5G  39% /media/windows

```
THEN (cat /etc/fstab)```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

```
FOR FLOPSY:
(ls -l /media/windows)```

tayo@ubuntu:~$ ls -l /media/windows
total 491300
-rwxr-xr-x   1 root root         0 2005-12-03 16:38 autoexec.bat
-rwxr-xr-x   1 root root       194 2005-12-03 16:29 boot.ini
-rwxr-xr-x   1 root root         0 2005-12-03 16:38 config.sys
drwxr-xr-x   7 root root      4096 2005-12-03 15:53 Documents and Settings
-rwxr-xr-x   1 root root 200790016 2005-12-03 16:46 hiberfil.sys
-r-xr-xr-x   1 root root         0 2005-12-03 16:38 io.sys
-r-xr-xr-x   1 root root         0 2005-12-03 16:38 msdos.sys
-r-xr-xr-x   1 root root     47580 2003-03-31 13:00 ntdetect.com
-r-xr-xr-x   1 root root    233632 2003-03-31 13:00 ntldr
-rwxr-xr-x   1 root root 301989888 2005-12-03 16:44 pagefile.sys
dr-xr-xr-x  18 root root      4096 2005-12-03 16:36 Program Files
drwxr-xr-x   3 root root      4096 2005-12-03 16:45 System Volume Information
drwxr-xr-x  35 root root      8192 2005-12-03 15:48 windows
 
```
FINALLY
(ls -ld /media/windows)```

tayo@ubuntu:~$ ls -ld /media/windows
drwxr-xr-x  2 root root 4096 2005-12-04 14:39 /media/windows

```
hope this helps

---

### Post by aysiu on 2005-12-04
Looks good to me.
Have you tried this? ```
sudo umount /media/windows
sudo mount -a
```

---

### Post by Bagleemo on 2005-12-04
I'm on Kubuntu Breezy w/ similar problem. 

1. Edited fstab as per [http://ubuntuguide.org/#mountunmountfat](http://ubuntuguide.org/#mountunmountfat)
2. Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/datadrive  vfat    iocharset=utf8,umask=000  0   0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
~

hda5 is the fat partition in question. 
Note: I didn't add a line for it since there already was one there.I just changed everything after vfat as per the ubuntuguide.

I can see the files, but get an error from Konqueror when I try to delete them:
"Access denied to /media/datadrive/(etc - the file I'm trying to delete.)"

---

### Post by Blaauw01 on 2005-12-04
I had the same problem this week. Able to see my vfat secondary harddisk but not able to write.

I got the following suggestion wich did the job for me.  I am now able to read and write.

change the command in /etc/fstab like following:

/dev/hda1 /mnt/windows vfat noauto,user,uid=<your user id>,gid=users

---

### Post by anil_robo on 2005-12-04
I followed [www.ubuntuguide.org](www.ubuntuguide.org) about how to mount windows partitions in Ubuntu, and have been able to get everything working right. HOwever, I know there can be problems when I write to NTFS partitions from Ubuntu. SO I have mounted NTFS read only, and have created a partition using FAT32 format so that I can keep my common data on it - both Ubuntu and WinXP can read and write on this partition - useful for keeping school projects etc. which need frequent editing from both WInXP and Ubuntu.

---

### Post by Bagleemo on 2005-12-09
Ahh: Found on another thread the proper values, which appear to be working for mounting my fat partition:

/dev/hda5 /media/datadrive vfat rw,uid=1000,gid=1000,exec,user 0 0

(my user ID is 1000 and my user's group is 1000 - might need different values if yours is different.)

---

