---
title: "Windows XP not booting GRUB Problems"
date: 2006-06-04
forum: Desktop Environments
---

### Post by gaza on 2006-06-04
Hi, here's the information on my hard drives, please help me get GRUB to boot my windows partition, I'm only being able to use the linux partition.

fdisk -l:
```
Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        4462    35832982+   f  W95 Ext'd (LBA)
/dev/hda2            4463        8286    30716280   83  Linux
/dev/hda3            8287        8318      257040   82  Linux swap / Solaris
/dev/hda5               2        4462    35832951    7  HPFS/NTFS
```

Grub menu:

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot


title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault		
makeactive
chainloader	+1



### END DEBIAN AUTOMAGIC KERNELS LIST

```

I get this message when I try to boot:

```

root (hd0,4)
Filesystem type unknown, partition type 0x7
savedefault
makeactive

Error 12: Invalid device requested

```

When I change the grub file to say **root (hd0,0)** I get the same error, except it says **partition type 0xf**.

So my WIndows is on that hda5. It's a partition of the same disk. Please help me out here.

Thanks. :)

---

### Post by randell6564 on 2006-06-05
You need to install 'grub' onto your windows partition in order to dual boot

When dual booting, in my experience, it's best to install 'Windoze' first, then 'Linux'.

---

### Post by bb002 on 2006-06-05
try changing 

```

title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault		
makeactive
chainloader	+1

```
to this
```

title		Microsoft Windows XP Professional
rootnoverify	(hd0,4)
savedefault		
makeactive
chainloader	+1

```

---

### Post by index_0@ya.com on 2006-06-05
did u know abt a bug in dapper grub,? tht ll simply erase the windows ntfs  partitions ? well it happened to me last night !

and discussed in this forum

---

### Post by Sutekh on 2006-06-05
[quote=gaza]
/dev/hda5               2        4462    35832951    7  HPFS/NTFS[/code] 

Grub menu:

```

title        Microsoft Windows XP Professional
root        (hd0,4)
savedefault        
makeactive
chainloader    +1

``` 
[/quote]Windows will not like being booted from any other partition than the first on the first disc.  You should be able to use GRUB to fool Windows into thinking such, by using the **map** commands.

Try using this to boot Windows
```
title        Microsoft Windows XP Professional
root        (hd0,4)
savedefault        
[B]map           (hd0,0) (hd0,4)
map           (hd0,4) (hd0,0)[/B] 
makeactive
chainloader    +1
```

---

### Post by randell6564 on 2006-06-05
[QUOTE=Sutekh]Windows will not like being booted from any other partition than the first on the first disc.  You should be able to use GRUB to fool Windows into thinking such, by using the **map** commands.

Try using this to boot Windows
```
title        Microsoft Windows XP Professional
root        (hd0,4)
savedefault        
[B]map           (hd0,0) (hd0,4)
map           (hd0,4) (hd0,0)[/B] 
makeactive
chainloader    +1
```[/QUOTE]

EXACTLY!  'MBR'

---

### Post by gaza on 2006-06-05
[QUOTE=Sutekh]

Try using this to boot Windows
```
title        Microsoft Windows XP Professional
root        (hd0,4)
savedefault        
[B]map           (hd0,0) (hd0,4)
map           (hd0,4) (hd0,0)[/B] 
makeactive
chainloader    +1
```[/QUOTE]

Thanks for the help :) , but it's still printing

```

root(hd0,4)
filsystem type unknown, partition type ox7
savedefault
map           (hd0,0) (hd0,4)
map           (hd0,4) (hd0,0)[/B] 
makeactive
chainloader    +1

Error 12:Invalid device requested

```

It's strange. I mean, Windows was already installed in the machine. Windows used 2 partitions in the same hard drive. I deleted one with the Ubuntu CD and installed. I had done it before and it worked.

---

### Post by gaza on 2006-06-05
Anyone? C'mon, I know you guys know how to solve this.

:D

---

### Post by randell6564 on 2006-06-05
[QUOTE=gaza]Thanks for the help :) , but it's still printing

```

root(hd0,4)
filsystem type unknown, partition type ox7
savedefault
map           (hd0,0) (hd0,4)
map           (hd0,4) (hd0,0)[/B] 
makeactive
chainloader    +1

Error 12:Invalid device requested

```

It's strange. I mean, Windows was already installed in the machine. Windows used 2 partitions in the same hard drive. I deleted one with the Ubuntu CD and installed. I had done it before and it worked.[/QUOTE]


You DELETED one of your windows partitions! This is suspect!  Also, do you have any type of partitioning software?

I would go in and set up partitions for ubuntu, reinstall and make sure to place 'grub' in 'MBR'.

There is no reason why you do not have the option to boot Windoze95. XP or ubuntu if 'grub' is where it is suppose to be.

---

### Post by sherlock-holmes on 2006-06-05
[QUOTE=gaza]Anyone? C'mon, I know you guys know how to solve this.

:D[/QUOTE]


use the ubuntu live CD and go up to the point where you install grub into the MBR... and then quit the installation... that would help... knoppix is a nice live cd to begin with .... ubuntu cd is also fine iguess...

---

### Post by Sutekh on 2006-06-05
I don't know if this link has has been updated for Dapper yet but it should help you reinstall GRUB...
 
 [Ubuntu Wiki - Recovering Ubuntu After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows")

Live CD is now the Desktop CD, the old Install CD is now the Alternate CD...

---

