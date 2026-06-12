---
title: "rm cannot remove file: Input/output error"
date: 2009-04-19
forum: General Help
---

### Post by BioGeek on 2009-04-19
Hi all,

I have [TimeVault]("https://wiki.ubuntu.com/TimeVault") as backup system, but recently it is giving me errors that it can't remove a snapshot directory. When I go into the offending directory, there is indeed a hidden file that i can't remove.

```
$ ls -al
ls: cannot access .IMG_8854.JPG.yyDFPb: Input/output error
total 20
drwxrwxrwx 1 root root  8192 2009-04-17 12:01 .
drwxrwxrwx 1 root root 12288 2009-04-17 12:01 ..
-????????? ? ?    ?        ?                ? .IMG_8854.JPG.yyDFPb
$ sudo rm -f .IMG_8854.JPG.yyDFPb 
[sudo] password for jeroen: 
rm: cannot remove `.IMG_8854.JPG.yyDFPb': Input/output error
```

How do I go about removing this file?

Thanks in advance.

---

### Post by mkrahmeh on 2009-04-19
can you remove the directory "rm -fr" ?
what is the output of ```
echo $?
```

---

### Post by BioGeek on 2009-04-19
> **mkrahmeh said:**
> can you remove the directory "rm -fr" ?


No:

```

$ cd ..
$ sudo rm -rf 2009_04_04_verjaardag_Katrien/
[sudo] password for jeroen: 
rm: cannot remove `2009_04_04_verjaardag_Katrien/.IMG_8854.JPG.yyDFPb': Input/output error
```
 

> what is the output of ```
echo $?
```

```
$ echo $?
1
```

---

### Post by mkrahmeh on 2009-04-19
uhh..forget about the echo thing (hate man pages that do not explain there exit codes)..

first, am afraid that the file is being accessed by other process (the timevault maybe) so try shutting it down

what is the output of 
```
file *file_name*
```

second, try to cd into the directory, and issue the find command to look for the file
```
find ./ -name *file_name*
```
then post back the echo's output

try a couple of commands on the file, like find, cat, chown.....
and look for any abnormalities, post back if you find anything
if nothing found, we may consult with the system logs (dont know how that might help :confused: )

---

### Post by shad0w_walker on 2009-04-19
Input/output errors generally appear when you have hardware problems. Sounds like you might be getting bad sectors. I'd look into running some SMART tests and perhaps, if they start showing problems, getting a new drive.

---

### Post by BioGeek on 2009-04-19
> **mkrahmeh said:**
> what is the output of 
```
file *file_name*
```


```
$ file .IMG_8854.JPG.yyDFPb 
.IMG_8854.JPG.yyDFPb: ERROR: cannot open `.IMG_8854.JPG.yyDFPb' (Input/output error)
```


[QUOTE=mkrahmeh]second, try to cd into the directory, and issue the find command to look for the file
```

find ./ -name file_name
```
then post back the echo's output[/QUOTE]

```
$ find ./ -name .IMG_8854.JPG.yyDFPb 
./.IMG_8854.JPG.yyDFPb
$ echo $?
0
```

[QUOTE=mkrahmeh]
try a couple of commands on the file, like find, cat, chown.[/QUOTE]
```

$ sudo chown jeroen:jeroen .IMG_8854.JPG.yyDFPb 
[sudo] password for jeroen: 
chown: cannot access `.IMG_8854.JPG.yyDFPb': Input/output error
$ cat .IMG_8854.JPG.yyDFPb 
cat: .IMG_8854.JPG.yyDFPb: Input/output error
$ hexedit .IMG_8854.JPG.yyDFPb 
hexedit: .IMG_8854.JPG.yyDFPb: Not a file.
```

[QUOTE=shad0w_walker]Input/output errors generally appear when you have hardware problems. Sounds like you might be getting bad sectors. I'd look into running some SMART tests and perhaps[/QUOTE]

After reading up on [S.M.A.R.T.]("http://en.wikipedia.org/wiki/S.M.A.R.T."), I installed smartmontools, but my 1 TB external hard drive fromLaCie (on which the onremovable file is) seems not supported.
```

$ sudo apt-get install smartmontools
$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000341ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18715   150328206   83  Linux
/dev/sda2           18716       19457     5960115    5  Extended
/dev/sda5           18716       19457     5960083+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x454c112b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121601   976760001    7  HPFS/NTFS


$ sudo smartctl -i /dev/sdb1
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Device: SAMSUNG  HD103UJ          Version: 
Serial number: 152D20329000
Device type: disk
Local Time is: Sun Apr 19 17:42:15 2009 CEST
Device does not support SMART
```

The externalhard drive holds all my pictures and backups, so I that the drive doesn't die on me. Any advice as to which other tools I could use?

Is there any other low level means by which I could remove that file?

---

### Post by unutbu on 2009-04-19
It looks to me like there is some NTFS filesystem corruption on /dev/sdb1.

Perhaps install ntfsprogs and run ntfsfix:
```

sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
```

---

### Post by shad0w_walker on 2009-04-19
SMART is not supported on external devices. You'd need to take out the drive and mount it in your system. Corrupt NTFS filesystems will not spit out I/O errors. They will give a warning when mounting and will mount either read only or not at all unless forced. 

Dispite it's name, ntfsfix does not fix a NTFS filesystem, it simply clears the journal and tells it that all is well so that it can mount cleanly on linux. It is only to be used when you know there isn't corruption on the system and you are just trying to plug and play a USB drive on a linux system.

---

### Post by mkrahmeh on 2009-04-20
> **unutbu said:**
> It looks to me like there is some NTFS filesystem corruption on /dev/sdb1.

+1
try to check your filesystem. first you need to unmount the offending filesystem, then run the command
```
e2fsck /dev/*drive*
```
supposedly the filesystem is ext2 or ext3

it might complain about the superblock, in this case:
```
dumpe2fs /dev/*drive* | grep -i superblock
```
in the output, take the number of the backup superblock, then repeat the check with -b flag 
```
e2fsck -b *number* /dev/*drive*
```

i recommend consulting the man pages of e2fsck and dumpe2fs for more info. remember: unmount the file system b4 proceeding.
gl

---

