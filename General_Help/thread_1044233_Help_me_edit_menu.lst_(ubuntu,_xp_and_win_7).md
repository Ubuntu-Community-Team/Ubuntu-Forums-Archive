---
title: "Help me edit menu.lst (ubuntu, xp and win 7)"
date: 2009-01-19
forum: General Help
---

### Post by aschwerin.moses on 2009-01-19
This is my fdisk -l (i have a IDE and a SATA hdd's)

>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        9728    62782020    f  W95 Ext'd (LBA)
/dev/sda5            3825        9728    47423848+   7  HPFS/NTFS
/dev/sda6            1913        3633    13823869+  83  Linux
/dev/sda7            3634        3824     1534176   82  Linux swap / Solaris

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04c404c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sdb2            1913        9728    62782020    f  W95 Ext'd (LBA)
/dev/sdb5            1913        4629    21824271    7  HPFS/NTFS
/dev/sdb6            4630        9728    40957686    7  HPFS/NTFS

and my menu.lst is

> ## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f4ef0cd6-e198-4281-abc3-724326b6e18a ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=f4ef0cd6-e198-4281-abc3-724326b6e18a ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

i have Windows 7 installed in **/dev/sdb1**

i did add the below, to the list..but it does not work.. 

> title		Microsoft Windows 7
root		(hd1,0)

how do i get this working.. helpppp...

---

### Post by ajgreeny on 2009-01-19
Try
```
title		Microsoft Windows 7
root		(hd1,0)
savedefault
makeactive
chainloader	+1 			 		
```instead of what you have.  I think it may need the extra three lines, the same as windows XP.  If it doesn't work, nothing is lost, but others will need to help you further.

---

### Post by aschwerin.moses on 2009-01-19
tried it with **savedefault** and **chainloader +1** .. did not use **makedefaul**t cause that will make both XP and Win 7 default option, read somewhere that it will corrupt grub

---

### Post by funkyFlash on 2009-01-19
What you have, sir, is precisely one metric ton of partitions!

[This thread]("http://ubuntuforums.org/showthread.php?t=1036547") has a similar issue, but not the same.  I was just wondering if there was weirdness with Windows 7, so I stumbled across that thread.

If Windows 7 splatted it's own loader on that disk, you can just have grub pass the torch to that drive:

```

title Microsoft Windows 7
root(hd1)
chainloader
```

Chainloader just says "this guy knows what to do with himself, ready go".

---

### Post by caljohnsmith on 2009-01-19
[QUOTE=aschwerin.moses]WARNING: GPT (GUID Partition Table) detected on '/dev/[COLOR="Red"]sdb[/COLOR]'! The util fdisk doesn't support GPT. Use GNU Parted.[/QUOTE]
You're sdb drive has a GPT (GUID Partition Table) according to fdisk, so did you deliberately use a GPT rather than a standard MS-DOS partition table on the sdb drive? GPTs are mostly used with Apple computers. You might still be able to boot Windows, but it would be a good idea to fix that if your sdb drive is supposed to use the standard MS-DOS partition table; otherwise you won't be able to change the partitions at any point. How about posting:
```
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```
And also, to check your sdb drive's MBR (Master Boot Record), how about doing:
```
sudo dd if=/dev/sdb count=70 | gzip -c > ~/Desktop/sdb.MBR.gz
```
That will create a really small "sdb.MBR.gz" file on your desktop which will just contain the binary information at the beginning of the drive involved with a GPT setup. Please attach that file to your next post by clicking the paper clip icon in the Ubuntu forum message box, and that way I can try and get a better idea of what might be wrong with your sdb drive's MBR. We can work from there if you want.

---

### Post by aschwerin.moses on 2009-01-19
> **funkyFlash said:**
> 

```

title Microsoft Windows 7
root(hd1)
chainloader
```



tried it, nogo.. it says Error 1: Filename must be either an absolute pathname or blocklist

---

### Post by aschwerin.moses on 2009-01-19
> ```
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```

```
-rwxrwxrwx 1 root root         24 2008-10-15 21:41 autoexec.bat
drwxrwxrwx 1 root root      20480 2009-01-20 03:12 Biblegateway
drwxrwxrwx 1 root root       4096 2009-01-12 05:49 Boot
-rwxrwxrwx 1 root root     377151 2008-12-13 12:33 bootmgr
-rwxrwxrwx 1 root root       8192 2009-01-12 05:49 BOOTSECT.BAK
-rwxrwxrwx 1 root root         10 2008-10-15 21:41 config.sys
drwxrwxrwx 1 root root          0 2008-12-13 05:28 Documents and Settings
drwxrwxrwx 1 root root          0 2009-01-19 03:51 Encarta
-rwxrwxrwx 1 root root  590450688 2009-01-19 20:56 hiberfil.sys
drwxrwxrwx 1 root root          0 2009-01-12 02:32 Intel
-rwxrwxrwx 1 root root 1101082624 2009-01-19 20:56 pagefile.sys
drwxrwxrwx 1 root root          0 2008-12-13 13:27 PerfLogs
drwxrwxrwx 1 root root       4096 2008-12-13 05:28 ProgramData
drwxrwxrwx 1 root root       4096 2009-01-11 16:43 Program Files
drwxrwxrwx 1 root root          0 2009-01-11 16:30 Recovery
drwxrwxrwx 1 root root          0 2009-01-11 16:31 $Recycle.Bin
drwxrwxrwx 1 root root          0 2009-01-19 03:46 RECYCLER
drwxrwxrwx 1 root root       4096 2009-01-16 08:58 System Volume Information
drwxrwxrwx 1 root root       4096 2009-01-19 18:58 User32Backup
drwxrwxrwx 1 root root       4096 2009-01-11 16:30 Users
drwxrwxrwx 1 root root      16384 2009-01-16 02:08 Windows

```


> ```
sudo dd if=/dev/sdb count=70 | gzip -c > ~/Desktop/sdb.MBR.gz
```



Well, i had mac installed in sda, im not sure why its showing in sbd.. how do i get it into ms-dos??

---

### Post by 73ckn797 on 2009-01-19
> **aschwerin.moses said:**
> tried it, nogo.. it says Error 1: Filename must be either an absolute pathname or blocklist

Shouldn't the drive be listed as (hd1,0)? You have (hd1).

---

### Post by caljohnsmith on 2009-01-19
I looked over the file you posted of your sdb drive's first track, and it does look like you have a few sectors with some remnants of a GPT for some reason. In order to fix your sdb drive so that it doesn't use GPT, try this:
```
sudo dd if=/dev/zero of=/dev/sdb seek=1 count=50
```
Then do:
```
sudo fdisk -lu
```
And please post the output. Also, in order to boot Windows, try this entry:
```
title Windows 7
rootnoverify (hd1,0)
map      (hd1) (hd0)
map      (hd0) (hd1)
chainloader +1
```
And let me know exactly what happens when you try the above entry from the Grub menu. We can work from there if you want.

---

### Post by aschwerin.moses on 2009-01-19
well, it working.. 

```
title Microsoft Windows 7
root(hd1,0)
chainloader    +1
```

this worked.. well thank you guys [:)]

---

