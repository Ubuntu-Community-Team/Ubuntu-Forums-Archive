---
title: "FAT32 &quot;funnies&quot; in Ubuntu/Nautilus"
date: 2006-02-27
forum: Desktop Environments
---

### Post by dpm on 2006-02-27
Hi,

am I missing something here? I thought FAT32 read/write support in Linux was something fairly stable and tested. In fact, I've got no problems when writing to mu USB drive.

However, when mounting my Windows partitions in Ubuntu:
```

# this is a part of my /etc/fstab file
/dev/hda1   /media/hda1    vfat         iocharset=utf8,umask=000    0  0 

``` 
I experience the following "problems":

1. Some folders within the partition are only readable but not writable. Curiously, this seems to happen only with those folders that have a special icon assigned in Windows. And I've also noticed that files that are marked as "system" in Windows are also read-only when mounted in Ubuntu. I'd like to have write access to all my windows files, but this does not seem to be possible at the moment on my system.

2. Nautilus/Ubuntu don't seem to get capital letters right when creating a folder. For example, when I create a folder named "NIN" in Nautilus, I momentarily get 2 folders, one named "nin" and another one named "NIN". Afterwards, "NIN" seems to vanish and I end up with the folder name in lower case.

Any ideas? More than problems these are just little inconveniences. The only thing that worries me is whether there's a chance of corrupting my FAT32 partition from Ubuntu, which would be no good! I'm just wondering if anyone else has experienced these same issues...

Thanks.

---

### Post by vbmaster on 2006-02-27
do you have windows in a fat32 partition?

---

### Post by dpm on 2006-02-27
Yes, I have windows in a FAT32 partition. Here's my configuration:

```
$ sudo fdisk -l


Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1287    10337796    c  W95 FAT32 (LBA)
/dev/hda2            1288       24321   185020605    f  W95 Ext'd (LBA)
/dev/hda5            1288        2562    10241374+  83  Linux
/dev/hda6            2563        3837    10241406   83  Linux
/dev/hda7            3838        5112    10241406   83  Linux
/dev/hda8            5113        6386    10233373+  83  Linux
/dev/hda9            6387        6450      514048+  82  Linux swap / Solaris
/dev/hda10           6451       24321   143548776    b  W95 FAT32

``` 
I dual boot windows and ubuntu. hda1 is the partition where windows is installed, hda5 is my Ubuntu partition, and hda10 is my "data" FAT32 partition. The problems I described in my first post occur for both hda1 and hda10.

---

### Post by vbmaster on 2006-02-27
In your fstab try to add "rw," before iocharset blá blá blá....

---

### Post by claes on 2006-02-27
And in the mount option part of /etc/fstab you could add uid=1000 or what you have as uid. Check with id command.

Claes

---

### Post by dpm on 2006-02-27
adding

```

/dev/hda10  /media/hda10    vfat         rw,iocharset=utf8,umask=000,uid=1000    0  0

``` 
to etc/fstab, unmounting and remounting did not make any difference. Still some files/folders are read-only, some are read/write, and still the same ones.

BTW, I don't think adding 'rw' before 'iocharset' is needed, since by looking at the man page for 'mount' it seems that the 'rw' option is enabled per default.

Any suggestions? As far as I can see, and as I said before, this seems to happen only to "special" folders and files, that is, those that have the system attribute set (under windows) or those that show up like an icon in explorer (also in windows).

---

### Post by dpm on 2006-03-02
Ok, I apologise for all the noise. The issue with read/write folders (pont 1 in my original post) seems to come from Windows. When I create a folder in my FAT32 partition from windows explorer, the folder has the read-only attribute set -that's what right clicking->File Properties shows. However, when looking at the attributes from the explorer, the R attribute is shown only, when, for example, the folder is customised by changing its default icon. That's why in ubuntu I only saw as read-only folders those where the default icon was changed. Anyway, enough of this talk, since this seems to be an issue with winblows...

However, the issue described in point 2 still remains, I don't seem to be able to control the Uppercase/Lowercase settings when naming a folder in Nautilus. Funnily enough, when I look at the folder in Windows, it has the right name I gave it originally from Nautilus. Could it be an issue with Nautilus displaying the name?

Any comments will be appreciated.

---

### Post by Garyu on 2006-03-02
I don't know about capital letters, but I had huge problems getting Ubuntu to accept swedish characters on my FAT32 (not windows) drive. 
```
/dev/hda5       /FTP            vfat    utf8,umask=000	0	0

```
this is what worked out for me in the end. so try skipping the "iocharset=" and see what happens. :cool:

---

### Post by dpm on 2006-03-14
bump

I found the solution. Reading the manual for mount, looking at the vfat section, the 'shortname' option is what I needed. I just had to change the default behaviour (lower), which was causing the issues described with case-changing to 'winnt', which basically keeps the casing of short filenames as well as displaying them the way they were created.

Quoting the kernel documentation for vfat (vfat.txt):

> NOTE: "iocharset=utf8" is not recommended. If unsure, you should consider the following option (utf8=<bool>) instead. 

Therefore, I didn't specify the iocharset explicitly and left it as the default (in my case iso8859-1, which is the charset my windows installation is also using). I only changed 'codepage' to 850 (Latin-1) instead of the default 437 (en-US) for 8.3 MS-DOS filenames. To see the defaults of the vfat module for these two settings, have a look at /boot/config-<yourkernel>, sections CONFIG_FAT_DEFAULT_CODEPAGE and CONFIG_FAT_DEFAULT_IOCHARSET

 Here's how I mounted one of my windows FAT32 partitions:

```
/dev/hdb1    /media/windows/D       vfat         shortname=winnt,codepage=850,umask=000,user  0  0
``` 
So far, that seems to work fine. And regarding the permissions issue, it seems as it is a windows-specific problem, so I'll keep looking somewhere else.

BTW, I think the wiki articles about mounting FAT32 partitions should also mention the 'shortname' option and the character set rather than instructing you to use iocharset=utf8. The fact that the short file names change from upper case to lower case and viceversa can be quite confusing (although mixed case works fine).

Well, I hope this can be of some use to someone.

Cheers.

---

