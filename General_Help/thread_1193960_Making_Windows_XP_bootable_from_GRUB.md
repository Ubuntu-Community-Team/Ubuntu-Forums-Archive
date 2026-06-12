---
title: "Making Windows XP bootable from GRUB"
date: 2009-06-22
forum: General Help
---

### Post by warnec on 2009-06-22
Hi. I know it's not regarding Ubuntu, but still think this would help some users is I get an answer. I remember Ubuntu community to be active and helpful from my Ubuntu usage days, and I hope you can help me one more time ;)

So, I'd like to use my GRUB to boot into Windows XP. I installed a Chakra distribution, and must say I love it, but it is still Alpha 3 Preview (omg) and doesn't have support for GRUB auto system detection. But after installing opensuse 11.1 it worked just fine, so I am sure it can be set manaully.

```

[warnec@chakra ~]$ sudo fdisk -lu
Has&#322;o:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    42078959    21039448+   7  HPFS/NTFS
/dev/sda2   *    42078960   625142447   291531744    f  W95 Ext'd (LBA)
/dev/sda5        42079085   147072239    52496577+   7  HPFS/NTFS
/dev/sda6       147072303   594004319   223466008+   7  HPFS/NTFS
/dev/sda7       594019503   614984264    10482381   83  Linux
/dev/sda8       614984328   621330001     3172837   83  Linux
/dev/sda9       621330003   625121279     1895638+  82  Linux swap / Solaris
[warnec@chakra ~]$

```

Now I know, this setup is totally f****** up and I want to entirely wipe it down as soon as Windows 7 final is available.

So, to clear this up - I've got 20GB Windows XP partition, which I don't use and it is the only primary - that's why I couldn't delete it, becuase the rest of the partitions are inside an extended partition (291GB). As I said, I don't use it, it has boot.ini file inside which points the PC to boot to the 50GB Windows XP partition, which I currently use (NOTE: I think I did it that way, but I'm not sure! It was a long time ago when I manually set up GRUB!). 

There is also one 220GB NTFS partition for my data storage and 3 partitions for home, swap and /.

I tried

```

title Windows XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1

```
```

title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader	+1

```
```

title Windows XP
root (hd0,4)
savedefault
makeactive
chainloader	+1

```

And all end in the same message:
```

Filesystem type unknown

Error 15: File not found

```
Or something similar.

Can you help me? BIG Thanks in advance ;)

---

### Post by swerdna on 2009-06-22
My money is on sda1, the (hd0,0) option. But it should be enough to use this:
> title Windows XP
rootnoverify (hd0,0)
chainloader	+1
If that doesn't work, mount sda1 somewhere and list the contents with a simple ```
ls -l /path_to/mount_point
```Let's see if the windows boot files are in there.

---

### Post by warnec on 2009-06-22
OK, I did:
```

[warnec@chakra ~]$ cd /mnt
[warnec@chakra mnt]$ sudo mkdir sda1

```
And then:
```

[warnec@chakra ~]$ sudo mount /dev/sda1 /mnt/sda1

```

And I get:
```

Can not enter folder /mnt/sda1/

```
In dolphin when I try to enter it. The same with 50GB partition.

```

[warnec@chakra ~]$ cd /mnt/sda1/
bash: cd: /mnt/sda1/: Brak dost&#281;pu

```
Brak dost&#281;pu = No access/Access denied, depending on the context. Don't know what's right here.

---

### Post by Entropy_Sam on 2009-06-22
Firstly, **rootnoverify**(...) is crucial - you can't boot an ntfs partition from grub with **root(...)**.
 
I'm a little confused about which partition is your XP partition, but  I can still advise...
 
Once you introduce extended patitions, figuring out how GRUB numbers your partitions is much more difficult from Linux. It's easier if you take a look from GRUB at boot time.
 
So reboot, and at the group menu, move the selector over your WinXP menu item and edit it.
 
Then edit the first line so it reads ```
rootnoverify(hd0,
``` and press Tab to use autocomplete. It should list all the partitions i can see from there. Your NTFS partitions will be listed as '**0x7**'.
 
If in doubt as to which is which, you could reboot a few times in a row, editing GRUB at boot time to read **rootnoverify(hd0,x)** until you find the value of x which correspons to the correct XP partition.
 
There's a chance you've already tried specifying the correct partition, but didn't use **rootnoverify**.
 
Hope that helps!

---

### Post by swerdna on 2009-06-22
> **warnec said:**
> OK, I did:
```

[warnec@chakra ~]$ cd /mnt
[warnec@chakra mnt]$ sudo mkdir sda1

```
And then:
```

[warnec@chakra ~]$ sudo mount /dev/sda1 /mnt/sda1

```

And I get:
```

Can not enter folder /mnt/sda1/

```
In dolphin when I try to enter it. The same with 50GB partition.

```

[warnec@chakra ~]$ cd /mnt/sda1/
bash: cd: /mnt/sda1/: Brak dost&#281;pu

```
Brak dost&#281;pu = No access/Access denied, depending on the context. Don't know what's right here.
Three things I can think of, the first being the most obvious:
[LIST=1]
[*]the NTFS mount command is:```
ntfs-3g /dev/sda1 /mnt/sda1
```
That might do it, if not then check out 2 and 3 below
[*]Check the directory sda1 exists with command```
 ls -l /mnt
```You should see like this:> drwxr-xr-x  2 root root  4096 2009-05-20 05:58 sda1What do you see?
[*]Check the device /dev/sda1 is not mounted already somewhere else with this command:```
df -Th
```
[/LIST]

---

### Post by warnec on 2009-06-22
OK, ntfs-3g solves it. 

But about the autocompletition thing - there are (0,0) (0,4) and (0,7) with 0x7 (if I remember correctly) and all of them give me error 15 (w/ rootnoverify, of course)

PS.:

My boot.ini file in sda1:
```

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional 1" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (on Volume 1)"

```

the partition(1) is the 20 GB one, and parition(2) is the 50 GB one.

---

### Post by swerdna on 2009-06-22
Well boot.ini is on sda1, but are the other bootloader files there, remember you were going to do this listing:```
ls -l /mnt/sda1
```

---

### Post by swerdna on 2009-06-22
OK, this is interesting:
[HTML]multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional 1" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (on Volume 1)"[/HTML]
Partition 2 was the original default first partition to be booted -- and it was booted off of sda1. Did you have two operating systems booting off the hard drive before Ubuntu -- and what were they?

Tell us, was it that originally, before Ubuntu, there were only three partitions on the drive? And all NTFS? and were they all primary partitions? [of course, that's not the case now, hence my question/s].

---

### Post by warnec on 2009-06-22
If I rember correctly, at first there was one primary 20 GB partition, and 300 GB extended partition for my data (all NTFS) then I decided I wanted to do a XP reinstall and wanted to make a seamless transition into new system, and was afraid I would forget to transfer some important file, and I decided to divide 300 GB partition into 250GB and 50GB, where 50GB would be for new XP. I didn't know anything about partitioning that time and didn't know I wouldn't be able to delete the 20GB one (I wanted to incorporate it into 250GB, to make 270GB volume in the future). 

Then I started to use Linux and took some free space from 250GB, making 10GB volume for '/', 3 GB for '/home' and about 1.5GB for 'swap' most of the time.  

After I swa that I am unable to remove the 20GB partition I decided to hide an option of booting it, so that the system looks into primary partition's boot.ini, and then is immidiately pointed to the 50 GB volume to boot.



PS.: Maybe there is some sort of GRUB LiveCD for me to automatically set it up?

PPS.: 
```

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

```
Points to the 50GB volume. I rember that, because I set that manually. 

PPPS.:
```

[warnec@chakra mnt]$ ls -l /mnt/sda1                                             
razem 1715                                                                       
drwxrwxrwx 1 root root      0 30.05.2008 18:19 $RECYCLE.BIN/                     
drwxrwxrwx 1 root root  16384 05.06.2008 19:12 $WIN_NT$.~BT/                     
drwxrwxrwx 1 root root      0 29.06.2008 17:01 AutoStitch/                       
drwxrwxrwx 1 root root   4096 30.05.2008 16:58 Boot/                             
drwxrwxrwx 1 root root   4096 28.07.2008 22:21 Documents and Settings/           
drwxrwxrwx 1 root root   4096 11.05.2008 16:56 Fraps/                            
drwxrwxrwx 1 root root      0 19.01.2007 19:58 Intel/                            
drwxrwxrwx 1 root root   4096 27.04.2008 16:13 LiveUpdate_Temp/                  
drwxrwxrwx 1 root root      0 22.04.2008 14:02 Logs/                             
drwxrwxrwx 1 root root      0 10.06.2008 21:59 Lxk700/                           
drwxrwxrwx 1 root root      0 14.02.2008 10:25 Media/                            
drwxrwxrwx 1 root root      0 22.11.2008 14:04 NVIDIA/                           
drwxrwxrwx 1 root root  24576 25.07.2008 14:13 Program Files/                    
drwxrwxrwx 1 root root      0 07.06.2008 14:59 RECYCLER/                         
drwxrwxrwx 1 root root      0 09.03.2009 16:57 SAMFILES/                         
drwxrwxrwx 1 root root   4096 22.01.2008 20:32 SeaTools for Windows/             
drwxrwxrwx 1 root root  12288 13.02.2008 18:33 Soldat/                           
drwxrwxrwx 1 root root   4096 07.06.2008 11:44 System Volume Information/        
drwxrwxrwx 1 root root  94208 16.09.2008 18:34 WINDOWS/                          
drwxrwxrwx 1 root root   8192 19.04.2009 16:36 WebCamNXPro/                      
-rwxrwxrwx 1 root root 262400 03.08.2004 23:00 $LDR$*                            
-rwxrwxrwx 1 root root      0 19.01.2007 19:18 AUTOEXEC.BAT*                     
-rwxrwxrwx 1 root root   8192 30.05.2008 16:58 BOOTSECT.BAK*
-rwxrwxrwx 1 root root    280 05.06.2008 19:11 Boot.BAK*
-rwxrwxrwx 1 root root   4952 22.07.2001 02:13 Bootfont.bin*
-rwxrwxrwx 2 root root  53248 28.04.2008 22:20 INFORMATYKA PROJEKT.doc*
-rwxrwxrwx 1 root root    198 20.03.2008 09:54 INSTALL.LOG*
-rwxrwxrwx 1 root root      0 19.01.2007 19:18 IO.SYS*
-rwxrwxrwx 2 root root    325 27.07.2008 21:00 Kopia boot.ini*
-rwxrwxrwx 1 root root      0 19.01.2007 19:18 MSDOS.SYS*
-rwxrwxrwx 1 root root  47564 04.08.2004 00:38 NTDETECT.COM*
-rwxrwxrwx 1 root root  13030 02.11.2008 11:55 PDOXUSRS.NET*
-rwxrwxrwx 1 root root    307 14.10.2008 22:00 boot.ini*
-rwxrwxrwx 1 root root 438840 02.11.2006 10:53 bootmgr*
-rwxrwxrwx 1 root root      0 02.02.2008 14:55 config.sys*
-rwxrwxrwx 2 root root      0 13.02.2008 19:23 logwmemory.bin*
-rwxrwxrwx 1 root root 251152 07.06.2008 13:17 ntldr*
-rwxrwxrwx 1 root root    173 19.10.2008 12:32 pdisdk.log*
-rwxrwxrwx 1 root root    184 19.10.2008 12:33 pivot.log*
-rwxrwxrwx 1 root root   1257 21.06.2009 18:48 sti.log*
-rwxrwxrwx 1 root root 469089 04.08.2004 01:17 txtsetup.sif*
[warnec@chakra mnt]$

```

PPPPS.: There are some Windows system files which could get you confused - it is because once I wanted to install new XP using CD put into to the DVD reader inside older XP (I know, confusing - what I mean, is I hoped to install 50 GB XP from 20 GB XP, without need of rebooting and using any non-GUI tools, I hoped it'd work like Wubi for Ubuntu, sort of - only GUI installer), but it told me to reboot and it wanted to continue installing process without GUI tools inside windows (so, like booting from CD), and I decided to boot normal 20GB XP and removed the option in boot.ini to boot the installer first, so I got only 20 GB system, but I left the temporary installer files there, because I didn't use the 20GB system anymore after that (I installed 50GB XP normally) and didn't care. ;)

PPPPPS.: Ask any questions if you are confused, and I am almost certainly sure you are. Sorry!

---

### Post by swerdna on 2009-06-22
I see that vista (or win7) has been involved. Can you describe that. And di it all boot OK after vista (or win7)?

---

### Post by dazman19 on 2009-06-22
Im about to chuck windows XP onto a second physical hard drive. 
I am quite worried about it writing its MBR loader over the top of GRUB. 

Do I,
A) disable the other disks in the BIOS and install windows then enable them and edit grub to boot windows.
B) Physically disconnect the disks that I don't need? 

I do realise because windows is on a seperate disk that is not disk 1 that I will have to do a virtual swap in grub. 

I am very concerned about overwriting grub because i know windows is naughty.

---

### Post by warnec on 2009-06-22
@ dazman19 - I think it would be wiser to make a separate topic for your question ;)


@ swerdna:

I am a little surprised by what you wrote. I remember I tried Vista once after it was released but I didn't like it - I removed i. I don't remember what kind of influence it had on the partition table. And If I remember correctly, I then overwrote Vista's boot code with 'fixmbr' to boot XP only (before I had Vista & XP)

---

### Post by warnec on 2009-06-22
I can't believe I haven't figured it out before :D
Simple:
```

title Windows XP
rootnoverify (hd0,0)
chainloader +1 

```
does the trick completely ;) All other additions just caused the issue.

Big thanks for support ! :)

---

### Post by swerdna on 2009-06-22
> **warnec said:**
> 
@ swerdna:

I am a little surprised by what you wrote. I remember I tried Vista once after it was released but I didn't like it - I removed i. I don't remember what kind of influence it had on the partition table. And If I remember correctly, I then overwrote Vista's boot code with 'fixmbr' to boot XP only (before I had Vista & XP)
OK, that's the way to go. I saw that vista left a thumbprint, that's all, and you've effectively nullified it, which is what I was concerned about, so that's not having an effect on booting.

---

### Post by swerdna on 2009-06-22
> **warnec said:**
> I can't believe I haven't figured it out before :D
Simple:
```

title Windows XP
rootnoverify (hd0,0)
chainloader +1 

```
does the trick completely ;) All other additions just caused the issue.

Big thanks for support ! :)
It quite went over my head that you didn't try post #2. I was working on the assumption that you tried it and it failed. Anyways -- glad you finally got it.

---

