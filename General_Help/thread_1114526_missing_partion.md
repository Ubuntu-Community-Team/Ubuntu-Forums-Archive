---
title: "missing partion"
date: 2009-04-02
forum: General Help
---

### Post by roadknight on 2009-04-02
i recently switched from a duel boot to pure Ubuntu. i had a 70gb fat32 partion i used for both systems. after i deleted xp and reinstalled ubuntu i cant acesss my fat32 partition. I had no problems accessing it before. i know its still there and i need to get to it it has all my media files and all my backup files on it please help.
```
I ran
(parted) print list,all
Model: ATA ST9120821AS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  905MB   905MB   primary   ext3         boot 
 2      905MB   12.4GB  11.5GB  primary   ext3              
 3      12.4GB  38.0GB  25.6GB  primary   ext2              
 4      38.0GB  120GB   82.0GB  extended                    
 5      38.0GB  108GB   70.2GB  logical   fat32             
 6      108GB   119GB   10.8GB  logical   ext2              
 7      119GB   120GB   1094MB  logical   linux-swap
```

```
ran sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37793778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         110      883543+  83  Linux
/dev/sda2             111        1509    11237467+  83  Linux
/dev/sda3            1510        4623    25013205   83  Linux
/dev/sda4            4624       14593    80084025    5  Extended
/dev/sda5            4624       13152    68509161    b  W95 FAT32
/dev/sda6           13153       14460    10506478+  83  Linux
/dev/sda7           14461       14593     1068291   82  Linux swap / Solaris
```


```
ran
(parted) check 5                                                          
Warning: The information sector has the wrong signature (0).  Select cancel for
now, and send in a bug report.  If you're desperate, it's probably safe to
ignore.
Ignore/Cancel? ignore                                                     
Fatal: Bad FAT: unterminated chain for \2009-0~1.TXT.  You should run dosfsck or
scandisk.
```


i do not have dosfsck or scandisk

---

### Post by ptn107 on 2009-04-02
Can't you just temporarily mount /dev/sda5 and copy your files from it?

```
# sudo mkdir -p /media/windows
# sudo mount -t vfat -o iocharset=utf8,umask=000 /dev/sda5 /media/windows
```

---

### Post by roadknight on 2009-04-02
well that helped some i got some of the stuff back but not all the folders are showing up mainly the media and backups are still missing along with a 15gb folder with World of Warcraft installed in it

also just found a folder called Trash-1000 and 2 files 2009-04-01 14.32.18 Crash.dmp and 2009-04-01 14.32.18 Crash.txt the .txt file is marked as executable

---

### Post by roadknight on 2009-04-02
Thanks for the help ptn107 it was more than i was able to do in 3 days of trying. guess ill just reformat the partition to ext2 and replace the stuff that can be replaced and mourn :cry: the loss of pictures that cant be replaced

---

### Post by ptn107 on 2009-04-02
Unmount the partiton:
```
# sudo umount /media/windows
```

and try this:
```
# sudo mount -t vfat -o iocharset=utf8,umask=007,uid=1000,gid=1000 /dev/sda5 /media/windows
```

while your in there just post the output of this after you mount the drive (I'm curious):
```
ls -l /media/windows
```

---

### Post by roadknight on 2009-04-02
ok tried that same results

this what came up

```
danny@Beast:~$ ls -l /media/windows
total 1888
-rwxrwx--- 1 danny danny 1688093 2009-04-01 14:32 2009-04-01 14.32.18 Crash.dmp
-rwxrwx--- 1 danny danny   47515 2009-04-01 14:32 2009-04-01 14.32.18 Crash.txt
drwxrwx--- 3 danny danny   16384 2009-03-30 15:43 dsl_files
-rwxrwx--- 1 danny danny   23860 2009-03-30 15:43 dsl.html
drwxrwx--- 3 danny danny   16384 2009-03-30 06:52 full-installation_files
-rwxrwx--- 1 danny danny   27284 2009-03-30 06:52 full-installation.html
-rwxrwx--- 1 danny danny      69 2009-03-28 19:43 puppy-4.00-k2.6.21.7-seamonkey.iso.md5.txt
-rwxrwx--- 1 danny danny       0 2009-03-30 16:56 puppy-4.2-k2.6.25.16-seamonkey.iso
-rwxrwx--- 1 danny danny   63224 2009-03-30 16:03 Screenshot-Connection Information-1.png
```

---

### Post by ptn107 on 2009-04-02
Does this show anything:
```
# ls -la /media/windows
```
This will show hidden files as well.

If not then I don't know what to tell ya.  There's just nothing else there.

---

### Post by roadknight on 2009-04-02
it looks pretty much the same to me... sadly i think the other stuff is just gone....

```
danny@Beast:~$ ls -la /media/windows
total 1944
drwxrwx--- 7 danny danny   16384 1969-12-31 18:00 .
drwxrwx--- 7 danny danny   16384 1969-12-31 18:00 .
drwxr-xr-x 5 root  root     4096 2009-04-02 20:47 ..
drwxr-xr-x 5 root  root     4096 2009-04-02 20:47 ..
-rwxrwx--- 1 danny danny 1688093 2009-04-01 14:32 2009-04-01 14.32.18 Crash.dmp
-rwxrwx--- 1 danny danny   47515 2009-04-01 14:32 2009-04-01 14.32.18 Crash.txt
drwxrwx--- 3 danny danny   16384 2009-03-30 15:43 dsl_files
-rwxrwx--- 1 danny danny   23860 2009-03-30 15:43 dsl.html
drwxrwx--- 3 danny danny   16384 2009-03-30 06:52 full-installation_files
-rwxrwx--- 1 danny danny   27284 2009-03-30 06:52 full-installation.html
-rwxrwx--- 1 danny danny      69 2009-03-28 19:43 puppy-4.00-k2.6.21.7-seamonkey.iso.md5.txt
-rwxrwx--- 1 danny danny       0 2009-03-30 16:56 puppy-4.2-k2.6.25.16-seamonkey.iso
-rwxrwx--- 1 danny danny   63224 2009-03-30 16:03 Screenshot-Connection Information-1.png
drwxrwx--- 2 danny danny   16384 2009-03-30 03:43 .Trash-1000
```

i do appreciate your help

---

### Post by ptn107 on 2009-04-02
You can dig through that trash folder if you want, but I think those files are gone.

---

