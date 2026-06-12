---
title: "Ubuntu won't load"
date: 2011-02-11
forum: Desktop Environments
---

### Post by Biscuity on 2011-02-11
Hi

My Ubuntu computer has not been used much, but when I booted it this morning, it won't boot into the OS.

Trying The Recovery mode option, it eventually gets to a message:

Gave up waiting for root device
missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/..long list of numbers... does not exist.

Any ideas please? :confused:

Edit: Booting to the Grub screen, I can see 3 different Ubuntu options & 3 recovery options. This computer only has Ubuntu 10.10 loaded & I had just followed the wizard setup from a CD. The computer has 1 SATA hard drive.

---

### Post by Krytarik on 2011-02-11
Did you modify the partitions of your disk after the installation?
It seems, it can't find the root directory ("/").

---

### Post by Biscuity on 2011-02-12
No I didn't modify the partitions. The only thing I have done with that pc is to connect 2 hard drives to the IDE controller & booting to one of the IDE hard drives so that I could use Easeus to image IDE disk1 to the new IDE disk2. The Ubuntu is sitting on SATA1.

---

### Post by Krytarik on 2011-02-12
So, to clearly get it, the disk(s) are set up the same like at the time of the install?

To get more info about your boot environment, boot with a LiveCD (InstallCD) and run those script, follow the instructions on the website:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then post its result here, in code-tags (#-button in the editor), or attach the text file.

---

### Post by Biscuity on 2011-02-12
Thanks, you are correct, nothing has changed apart from my running 2 disks on the IDE controller to do a image copy with Eraseus. I ran Erasus from one of the IDE disks running XP.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders, total 234493056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   228,487,167   228,485,120  83 Linux
/dev/sda2         228,489,214   234,491,903     6,002,690   5 Extended
/dev/sda5         228,489,216   234,491,903     6,002,688  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda2: PTTYPE="dos" 
/dev/sda5        9e44d8e1-4f6c-449e-898d-24b6e2352174   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  01 e5 9a 40 02 1e 83 3d  ea ef 60 6e c4 cf 6d 2c  |...@...=..`n..m,|
00000010  77 f1 9d c6 40 78 f3 14  e1 3e 94 fb b8 6d 1f 5c  |w...@x...>...m.\|
00000020  09 15 c6 e4 23 32 ca 3e  ea e3 d2 b4 8a b2 21 a6  |....#2.>......!.|
00000030  cb 02 e1 8d ba 47 68 37  20 eb 29 18 38 3e bf e1  |.....Gh7 .).8>..|
00000040  44 6b 14 72 3c 52 44 f1  02 33 bf 69 2c 3d c7 af  |Dk.r<RD..3.i,=..|
00000050  d2 84 ac ee 1c dd cb 5a  3c b0 1d 6d 61 95 c9 83  |.......Z<..ma...|
00000060  19 33 11 8f cc 7a 9a 15  7c f8 ee 4b ee 01 09 da  |.3...z..|..K....|
00000070  54 70 06 7b d2 e6 72 65  24 98 90 ca 0b c3 3f 94  |Tp.{..re$.....?.|
00000080  1a 12 3c a5 94 f4 92 9f  ae 47 70 b7 71 b4 aa ca  |..<......Gp.q...|
00000090  ea a0 08 57 af e3 53 ad  cd 34 6e c4 86 e0 6a 51  |...W..S..4n...jQ|
000000a0  a4 77 32 32 98 d4 05 cb  11 b4 0f a5 3a e5 a2 bb  |.w22........:...|
000000b0  9a 05 86 35 81 e1 6c a4  ac d8 56 c8 ea 4f f9 c5  |...5..l...V..O..|
000000c0  29 46 e6 5a 73 15 13 cd  8e 63 0c 32 a1 8d 8f cc  |)F.Zs....c.2....|
000000d0  76 9c 9f a5 5c 86 5b 76  bd b8 31 a3 db b2 91 f3  |v...\.[v..1.....|
000000e0  31 ea 3d a9 c1 de f1 37  b2 ea 32 78 e3 fb 29 76  |1.=....7..2x..)v|
000000f0  73 1c 6f 90 63 23 af f8  d3 b5 58 e0 92 3b 09 00  |s.o.c#....X..;..|
00000100  91 6e 20 7c a8 43 c3 83  d8 fa d4 b4 e2 43 56 2f  |.n |.C.......CV/|
00000110  5f 29 33 24 5f 6f 26 69  38 68 18 70 bf 43 54 ed  |_)3$_o&i8h.p.CT.|
00000120  59 66 51 e5 92 21 1d 1c  9e 94 ef a6 a5 45 77 24  |YfQ..!.......Ew$|
00000130  8a 78 c6 a2 19 e2 1e 58  18 0b d8 fe 74 d7 b7 b3  |.x.....X....t...|
00000140  9d 27 5c ab 2b 36 f2 8d  fe 15 2a 2c c1 c9 32 39  |.'\.+6....*,..29|
00000150  5a da 46 78 c4 81 ae 1c  0c a0 f4 14 5b ac 31 ea  |Z.Fx........[.1.|
00000160  ce 25 2c e3 18 18 ed 49  46 db 97 75 25 a9 66 f9  |.%,....IF..u%.f.|
00000170  96 da c9 ee 2d 98 7d a4  8f 98 7f 0e 3f c6 a1 d3  |....-.}.....?...|
00000180  0d d3 5a 16 b2 8e 53 bf  97 97 76 0c 60 d1 6b 82  |..Z...S...v.`.k.|
00000190  7c ba 12 4b 1b cb 79 b7  61 df 8f bc 7d 3d aa b2  ||..K..y.a...}=..|
000001a0  c5 2d b4 30 98 49 b8 b8  04 ef 04 93 b4 55 c5 6a  |.-.0.I.......U.j|
000001b0  5f 99 ab 1d dc 57 da 0c  96 d0 db 79 17 09 00 fe  |_....W.....y....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 5b 00 00 00  |............[...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Krytarik on 2011-02-12
Honestly, that doesn't look very good. I didn't see such an output of the script during my time at UF, though as you can see that's not that long, but intense. I'm surprised that Grub can even find its config file to display the menu.

How did you install Ubuntu in the first place?
Can you see the content of the system partition when running the LiveCD?
Is any data on it you need to extract before doing a fresh install?

---

### Post by Biscuity on 2011-02-13
Hi

I installed Ubuntu as a fresh installation using the Live CD. There is no important data on the pc. I understand that I must either reinstall Ubuntu, or go back to Windows. I must admit that I'm concerned with how unreliable Ubuntu appears to be. These problems I cannot fix on my own, but need help from kind people like yourself, mean that I don't think that I can continue with Ubuntu. :(

---

### Post by Krytarik on 2011-02-13
> **Biscuity said:**
> 
I installed Ubuntu as a fresh installation using the Live CD. There is no important data on the pc. I understand that I must either reinstall Ubuntu, or go back to Windows. I must admit that I'm concerned with how unreliable Ubuntu appears to be. These problems I cannot fix on my own, but need help from kind people like yourself, mean that I don't think that I can continue with Ubuntu. :(
I want to be absolutely clear here, that your partition issue is most probably not caused by Ubuntu, but may be the result of some kind of disk failure!

If you believe, you will have lasting success by reverting to Windows, then go on, good luck! Honestly, I mean it as such.

---

### Post by Biscuity on 2011-02-13
Thanks for your help.

I've wiped the disk & installed Windows 7. At least I know what I'm doing with Windows. :cool:

---

### Post by cerke on 2011-03-25
Hi guys,

I have the exact same problem.
I'm a big linux fan and I know that this problem is not caused by linux.
actualy, I know exactly what caused it: devil windows!!! :(

so, this is the problem:

when I try to boot my ubuntu maverick 10.10. it sayz:

Gave up waiting for root device
missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/..long list of numbers... does not exist.

before I tried to install windows xp as dual boot with ubuntu, everything was ok.
then xp ate my grub. I tried to reinstall it, but in the proces, my kernel image disapeared. -.-'
so now I can't acces to my data. :(
now I just want to extract my data and then make a clean ubuntu install...
can U help me please?? 

here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   445,990,911   445,988,864  83 Linux
/dev/sda2         445,996,530   468,519,659    22,523,130   7 HPFS/NTFS
/dev/sda3         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda2        A20C033E0C030CCB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4cc084f5-6cac-4616-b747-31964013701f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda2        /media/A20C033E0C030CCB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

thanks in advance! :)

---

### Post by Krytarik on 2011-03-25
@cerke: That looks indeed not really good! It seems like the Windows install screwed up the filesystem of your root partition. Because of that *all* your files aren't immediately accessible, including your home directory.

Boot with a LiveCD/InstallCD and try to fix the filesystem with GParted. If that is successful, you should also be able again to boot Ubuntu. If that fails, try to recover it with "Testdisk".

Good luck!

---

### Post by cerke on 2011-03-25
> **Krytarik said:**
> @cerke: That looks indeed not really good! It seems like the Windows install screwed up the filesystem of your root partition. Because of that *all* your files aren't immediately accessible, including your home directory.

Boot with a LiveCD/InstallCD and try to fix the filesystem with GParted. If that is successful, you should also be able again to boot Ubuntu. If that fails, try to recover it with "Testdisk".

Good luck!
 thanks krytarik.
there's only one problem: I don't know how to do that.
this is my first time that something like that happened, so can u please tell me how to do that with gparted?

thanks :p

---

### Post by Krytarik on 2011-03-25
First, boot with the InstallCD, choose "Try Ubuntu...".
- launch GParted, you should find it in "System -> Administration"
- right-click at your "sda1" partition
- choose "Check..."
- let it try doing its job

---

### Post by cerke on 2011-03-25
tried it. doesn't work... :(
so the next thing would be Testdisk.
what do I do with it exactly?

oh, and one more question:
could I solve this problem by installing a new kernel?

edit: I don't want to dublepost so I will just edit this one.
vielen dank krytarik for the help so far, I hope I'm not too anoying. :)
I will get back to this problem again tommorow...have to go now.
cheers!

---

### Post by Krytarik on 2011-03-25
> **cerke said:**
> tried it. doesn't work... :(
so the next thing would be Testdisk.
what do I do with it exactly?
 What exactly did you see in GParted? Did it show any errors?

You can use Testdisk to recover a inadvertedly deleted partition, among other things. But if the partition has been formatted and GParted doesn't show any errors, we won't have any luck with it. Testdisk is in the official repos, if you can establish an internet connection within the LiveCD, you can simply install it with Synaptic.

A word of caution: You need to be extremely careful when using Testdisk! Any careless action is potentially hazardous, meaning complete data loss! Although in your case, it can almost only get better.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
> **cerke said:**
> 
oh, and one more question:
could I solve this problem by installing a new kernel?

No, because there is currently nothing to install it to. There is no system at all currently.

---

### Post by cerke on 2011-03-26
well, GParted says this:
[http://ubuntuforums.org/attachment.php?attachmentid=187171&stc=1&d=1301157606](http://ubuntuforums.org/attachment.php?attachmentid=187171&stc=1&d=1301157606)
so I supose GParted can do nothing.

now I got Testdisk and I'm going to try it.
there's a bunch of tutorials so I'm just gonna follow one and see where thoes it lead me...

edit: tried to run testdisk, but it cotinuously repeats: permmision denied!
I tried sudo, sudo -s, nothing helps...
got the testdisk-6.12-WIP.
any ideas?

---

### Post by tushar maroo on 2011-03-26
> **cerke said:**
> Hi guys,

I have the exact same problem.
I'm a big linux fan and I know that this problem is not caused by linux.
actualy, I know exactly what caused it: devil windows!!! :(

so, this is the problem:

when I try to boot my ubuntu maverick 10.10. it sayz:

Gave up waiting for root device
missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/..long list of numbers... does not exist.

before I tried to install windows xp as dual boot with ubuntu, everything was ok.
then xp ate my grub. I tried to reinstall it, but in the proces, my kernel image disapeared. -.-'
so now I can't acces to my data. :(
now I just want to extract my data and then make a clean ubuntu install...
can U help me please?? 

here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Fat16
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   445,990,911   445,988,864  83 Linux
/dev/sda2         445,996,530   468,519,659    22,523,130   7 HPFS/NTFS
/dev/sda3         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)
/dev/sda2        A20C033E0C030CCB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4cc084f5-6cac-4616-b747-31964013701f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda2        /media/A20C033E0C030CCB  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

thanks in advance! :)
to extract your data from any o.s. you can boot the live-disk of ubuntu and extract the data out of it..........:)

---

### Post by Krytarik on 2011-03-26
> **cerke said:**
> well, GParted says this:
[http://ubuntuforums.org/attachment.php?attachmentid=187171&stc=1&d=1301157606](http://ubuntuforums.org/attachment.php?attachmentid=187171&stc=1&d=1301157606)
so I supose GParted can do nothing.
The screenshot looks promising. Can you access its contents with the LiveCD?
> **cerke said:**
> 
edit: tried to run testdisk, but it cotinuously repeats: permmision denied!
I tried sudo, sudo -s, nothing helps...
got the testdisk-6.12-WIP.
any ideas?
"sudo testdisk" should work. Please post the entire error message.

Why "6.12-WIP"? You should get this one:
[http://packages.ubuntu.com/maverick/testdisk](http://packages.ubuntu.com/maverick/testdisk)

---

### Post by cerke on 2011-03-27
@tushar maroo: tried that allready, but the content is not accessible...
@krytarik: I can't access to the partition because it seems it can't be mounted.
GParted says that the volume is not mounted, there's no mount point in home/media/ so nothing from that partition is visible.

ok, installed the testdisk, ran it, it found my disk with the correct size, selected the format, selected 'analyse' and testdisk says this: [http://ubuntuforums.org/attachment.php?attachmentid=187253&stc=1&d=1301221881](http://ubuntuforums.org/attachment.php?attachmentid=187253&stc=1&d=1301221881)
Now I ran 'quick search': [http://ubuntuforums.org/attachment.php?attachmentid=187255&stc=1&d=1301222369](http://ubuntuforums.org/attachment.php?attachmentid=187255&stc=1&d=1301222369)
Found my lost partition (the second one), tried to access the primary files and here's what I got: 
[http://ubuntuforums.org/attachment.php?attachmentid=187256&stc=1&d=1301223510](http://ubuntuforums.org/attachment.php?attachmentid=187256&stc=1&d=1301223510)
It seems that I can't access them so I ran 'deep search' and almost instantaniously an error popped out:
[http://ubuntuforums.org/attachment.php?attachmentid=187257&stc=1&d=1301223715](http://ubuntuforums.org/attachment.php?attachmentid=187257&stc=1&d=1301223715)
Now I'm waiting for deep search to do it's thang. :)

---

### Post by cerke on 2011-03-27
deep search finished his work and I think that Testdisk thinks that I'm stupid.
the analyser found the right disk/partition and it's size is 250 GB.
now check what deep search got:
[http://ubuntuforums.org/attachment.php?attachmentid=187262&stc=1&d=1301229379](http://ubuntuforums.org/attachment.php?attachmentid=187262&stc=1&d=1301229379)

it found 10 new partitions, first two 228 GB/ 212 GiB, and the rest are 239 GB/ 223 GiB.
what does this mean?:confused:

(actually, it found a hundred of partitions like that. I scrolled down, but there's too much of them...)

---

### Post by Krytarik on 2011-03-27
When you are at this screen:
[http://ubuntuforums.org/attachment.php?attachmentid=187255&stc=1&d=1301222369](http://ubuntuforums.org/attachment.php?attachmentid=187255&stc=1&d=1301222369)

- select the partitions marked with "D" and use the left/right arrow keys to change their 'characteristics', both to "P", like described at the very end of this guide: [http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html") (I posted it earlier)

- when all partitions are set correctly, all "P", press "Enter"

- then choose [Write], similar like in this screen:
[http://ubuntuforums.org/attachment.php?attachmentid=187256&stc=1&d=1301223510](http://ubuntuforums.org/attachment.php?attachmentid=187256&stc=1&d=1301223510)

Good luck!

---

### Post by cerke on 2011-03-27
it won't allow me to select all with 'P'.
it says: STRUCTURE: BAD-invalid partition structure, and can't write it.

so I checked the NTFS partition with 'D' and then it wrote it.
I supose I should change the type of the partition, one of them at least.
but I don't know wich...
[http://ubuntuforums.org/attachment.php?attachmentid=187284&stc=1&d=1301252428](http://ubuntuforums.org/attachment.php?attachmentid=187284&stc=1&d=1301252428)

now I want to mark my ubuntu partition as 'boot', but GParted won't start.
because of that linux won't load...

---

### Post by Krytarik on 2011-03-27
Could you please post a screenshot of how it looks now, in Testdisk!?

---

### Post by cerke on 2011-03-27
> **Krytarik said:**
> Could you please post a screenshot of how it looks now, in Testdisk!?

I did post the screenshot in the post above.
maybe ur looking for this:

---

### Post by Krytarik on 2011-03-27
> **cerke said:**
> I did post the screenshot in the post above.
maybe ur looking for this:
I wanted to be sure which partition you marked with "D".

Try to mark the second partition as bootable, via the "change type" dialog. But that won't fix the partition table.

Please choose the [Advanced] option at startup of Testdisk, check what is in there, post screenshots.

---

### Post by cerke on 2011-03-27
yeah, ur right. making it bootable does not solve the problem...

the first one in 'advanced' is this:[http://ubuntuforums.org/attachment.php?attachmentid=187303&stc=1&d=1301258628](http://ubuntuforums.org/attachment.php?attachmentid=187303&stc=1&d=1301258628)
it's type is MS Data and unknown

second: [http://ubuntuforums.org/attachment.php?attachmentid=187304&stc=1&d=1301258628](http://ubuntuforums.org/attachment.php?attachmentid=187304&stc=1&d=1301258628)
type MS Data and NTFS probably windows bootable

third: [http://ubuntuforums.org/attachment.php?attachmentid=187305&stc=1&d=1301258628](http://ubuntuforums.org/attachment.php?attachmentid=187305&stc=1&d=1301258628)
type linux swap and unknown

what can I do here?

---

### Post by Krytarik on 2011-03-27
The (now) first one should be ext4/Linux or such, as I conclude, right? Can you change it?

And "Linux Swap" should be something accordingly, try to change it as well.

---

### Post by oldfred on 2011-03-27
Your boot script showed ambivalent result.

See this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

---

### Post by cerke on 2011-03-28
changed the types, and then tried the procedure with testdisk once more.
now something changed. it seems like testdisk changed the types by himself.
the previous ext4 partition was broke into two now: one unallocaled and one NTFS on /dev/sda1 wich should be actually the ext4 I guess.
[http://ubuntuforums.org/attachment.php?attachmentid=187351&stc=1&d=1301296888](http://ubuntuforums.org/attachment.php?attachmentid=187351&stc=1&d=1301296888)

the testdisk after 'analyse' shows 4 partitions:
1. MS Data NTFS 40GB/37 GiB
2. MS Data ext4 228GB/212GiB
3. MS Data NTFS 11GB/10GiB
4. Linux Swap 10 GiB

the first one should not be there...
now I'm confused.:(

---

### Post by cerke on 2011-03-28
oh, and one more thing.
tried what oldfred said and this is the result:

[http://ubuntuforums.org/attachment.php?attachmentid=187352&stc=1&d=1301298046](http://ubuntuforums.org/attachment.php?attachmentid=187352&stc=1&d=1301298046)

I suppose that this is the fault of what was I combining with the testdisk..

---

### Post by Krytarik on 2011-03-28
> **cerke said:**
> changed the types, and then tried the procedure with testdisk once more.
now something changed. it seems like testdisk changed the types by himself.
the previous ext4 partition was broke into two now: one unallocaled and one NTFS on /dev/sda1 wich should be actually the ext4 I guess.
[http://ubuntuforums.org/attachment.php?attachmentid=187351&stc=1&d=1301296888](http://ubuntuforums.org/attachment.php?attachmentid=187351&stc=1&d=1301296888)

the testdisk after 'analyse' shows 4 partitions:
1. MS Data NTFS 40GB/37 GiB
2. MS Data ext4 228GB/212GiB
3. MS Data NTFS 11GB/10GiB
4. Linux Swap 10 GiB

the first one should not be there...
now I'm confused.:(
Both of that correspond with
a) each other
b) earlier statements of Testdisk (look back)

But GParted initially showed one big ext4 partition instead of a smaller partition and a bigger one.

It doesn't seem to get any better, right!? It seems like something messed up the partition table and broke up a single ext4 partition into two parts, even before we started, if it really wasn't there before. Are you sure about that?

Normally it is possible to have up to 4 primary partitions, but we got an error when we initially tried to set it that way. Also GParted initially showed the Linux-Swap partition as logical partition, which may have a reason. Please try to set it that way with Testdisk, use the arrow keys therefore at the respective screen, you may need to "add partition" before, choose "Extended Partition" or similar then. Also try to set the ext4 partition as bootable.

Also, what does
```
fdisk -l
```show?

---

### Post by cerke on 2011-03-29
> **Krytarik said:**
> 

It doesn't seem to get any better, right!? It seems like something messed up the partition table and broke up a single ext4 partition into two parts, even before we started, if it really wasn't there before. Are you sure about that?

Normally it is possible to have up to 4 primary partitions, but we got an error when we initially tried to set it that way. Also GParted initially showed the Linux-Swap partition as logical partition, which may have a reason. Please try to set it that way with Testdisk, use the arrow keys therefore at the respective screen, you may need to "add partition" before, choose "Extended Partition" or similar then. Also try to set the ext4 partition as bootable.

Also, what does
```
fdisk -l
```show?

```
fdisk -l
``` shows nothing.
that's weird...:confused:

well I'm almost 95 % sure that in the beginning was only a big ext4 partition, not two smaller.

as for the testdisk, it won't allow me to change partition type to logic..
only D and P choices are available.
and there's no ''exstended partition'' type. maybe sth else?
tried to make ext4 bootable, but every time I exit testdisk, it returns to the previonus state by himself.

it seems that this case is desperate...I'm on the brink of quiting...:(

---

### Post by Krytarik on 2011-03-29
> **cerke said:**
> 
as for the testdisk, it won't allow me to change partition type to logic..
only D and P choices are available.
Yeah, I was afraid of that, since we only see those captions in the menus, but I was hoping that that depends on the currently set characteristics. Then we need to create an extended partition before.
> **cerke said:**
> 
and there's no ''extended partition'' type. maybe sth else?
 When you are at this screen and you choose "add partition", what comes up?:
[http://ubuntuforums.org/attachment.php?attachmentid=187287&d=1301254294](http://ubuntuforums.org/attachment.php?attachmentid=187287&d=1301254294)
> **cerke said:**
> tried to make ext4 bootable, but every time I exit testdisk, it returns to the previonus state by himself.

You need to "Write" the partition table each time after you made changes.

Do you have any important, irrecoverable data on the disk?

---

### Post by Krytarik on 2011-03-30
If you want to try to create an image of your system partition at this point, use Clonezilla for that. Burn a bootable CD of it, and try different clone methods, at least "dd" may work, you need of course another disk therefore:

[http://www.clonezilla.org/](http://www.clonezilla.org/)

Good luck!

---

### Post by cerke on 2011-03-30
ok, this is what I get if I try to add a new partition:
(screenshots in the attachment)

unfortunately, I have all my college work on this disk and a lot of pictures.
everything else I can download again, but that I can't.

because of that I got an idea: ordered a new hard disk on which I will install a fresh OS; this one I will take out and put aside. and if I manage to recover data from it in some reasonable time, that disk will be used as a back-up disk. (never again without a back-up!)

even if none of this works, thank you very much Krytarik for all your efforts.
I appreciate this. :)

---

### Post by oldfred on 2011-03-30
Fortunately you ran boot script, as it printed out your partition table. I think your original problem was the ambivalent result issue.

```
Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   445,990,911   445,988,864  83 Linux
/dev/sda2         445,996,530   468,519,659    22,523,130   7 HPFS/NTFS
/dev/sda3         468,523,006   488,396,799    19,873,794   5 Extended
/dev/sda5         468,523,008   488,396,799    19,873,792  82 Linux swap / Solaris

```

You can manually rebuild from that.

The above is not quite the same format but all the info is there to calculate what this would be:

Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt
Then you can restore it:
Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

You may want to try this first. It is another way to fix or repair partition tables. I have not used it, but those that had overlapping partitions or other issues have had it work for them.

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Krytarik on 2011-03-30
> **cerke said:**
> ```
fdisk -l
``` shows nothing.
that's weird...

Ah, I just yet noticed it, one needs to use 'sudo' for it, I didn't mind that.

So the correct command is:
```
sudo fdisk -l
```
But I guess we should begin from scratch again: Please do a fresh "Analyse" with Testdisk, then change the characteristics of at least the first three stated partitions to "Primary", "P", and try again to change those of "Linux Swap" to "L", if that again isn't possible then to "P".

After you've done so, take a screenshot.

Then run the mentioned command.

Post its output, alongside the screenshot of Testdisk.

Also, I read the first thread mentioned by *oldfred*, and it seems like we are far away from the end of the road, everything seems still possible.

I also took a quick look at "FixParts". You should try it first, like *oldfred* suggested, after doing the above mentioned steps. But make sure to backup the partition table first, like described in its guide. This way we can't make it worse with the next steps.

---

### Post by cerke on 2011-03-31
I got some free time now so I will try with what oldfred said.
here are some screenshots that u requested:
[COLOR=black]http://ubuntuforums.org/attachment.php?attachmentid=187660&stc=1&d=1301585598 (before testdisk changes)
[http://ubuntuforums.org/attachment.php?attachmentid=187664&stc=1&d=1301587811](http://ubuntuforums.org/attachment.php?attachmentid=187664&stc=1&d=1301587811) (testdisk screen before ''write'') - for some reason I can't change 'linux swap' to 'L' so it's 'P' for now

after tesdisk command ''fdisk'' still says exact the same...

now I'm going to do a backup like oldfred said and then proceed with the procedure.
hopefully, this will be it.  :-/
[/COLOR]

---

### Post by oldfred on 2011-03-31
Now you are showing gpt? I did not  see that in the original boot script or did the ambivalent result confuse the boot script.

If it is really gpt then you need gdisk & gsfdisk. Do not use the copies from synaptic but download the latest versions from link below.

if it is not gpt:
Remove old parts of gpt
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

sudo parted /dev/sda unit s print
gdisk -l /dev/sda

---

### Post by cerke on 2011-04-03
the problem is that I really am not sure if it was originally GPT...
but after running a few scripts that U posted earlier it seams that some improvements show, so I can suppose that it was gpt.

right now I'm a little preoccupied  with my exams so when I catch some free time I'll sure try that.

thanks for the tips oldfred

---

### Post by cerke on 2011-04-04
ok, after I did a backup of my partition table based on gpt I zapped gpt with sgdisk and this is the result:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009d7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   187510679    93754316   83  Linux
/dev/sda2       187510680   398283479   105386400    f  W95 Ext'd (LBA)
/dev/sda5       193505823   398275919   102385048+   7  HPFS/NTFS
/dev/sda6       187510806   193502924     2996059+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 3985 MB, 3985637376 bytes
128 heads, 42 sectors/track, 1448 cylinders, total 7784448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x033f9b22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           8     7784447     3892220    b  W95 FAT32

``````
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=187508632, Id=83, bootable
/dev/sda2 : start=187510680, size=210772800, Id= f
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=193505823, size=204770097, Id= 7
/dev/sda6 : start=187510806, size=  5992119, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=        8, size=  7784440, Id= b, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

``````
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA FUJITSU MHZ2250B (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  96.0GB  96.0GB  primary   fat16        boot
 2      96.0GB  204GB   108GB   extended               lba
 6      96.0GB  99.1GB  3068MB  logical
 5      99.1GB  204GB   105GB   logical

``````
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.7.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************

Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 8BA59701-7C0F-4CCB-8038-3D60B4782562
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 1-sector boundaries
Total free space is 90126253 sectors (43.0 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       187510679   89.4 GiB    0700  Linux/Windows data
   5       193505823       398275919   97.6 GiB    0700  Linux/Windows data
   6       187510806       193502924   2.9 GiB     8200  Linux swap

```Gparted says this:
[http://ubuntuforums.org/attachment.php?attachmentid=188053&stc=1&d=1301901402](http://ubuntuforums.org/attachment.php?attachmentid=188053&stc=1&d=1301901402)

it still doesn't look as it should, but maybe it just needs rebooting.
now I will reboot and then we will see.

---

### Post by cerke on 2011-04-04
and after rebooting still nothing..

only an error message appears:

NTLDR is missing
Press any key to restart
(then I press a key)
Non-System disk or disk error
replace and strike any key when ready

I'm still confused. not sure if originally there was gpt or msdos (my disk is bought brand new, not used, first there was all kinds of windows installed on it and as last ubuntu 10.10)
maybe testdisk made this confusion with gpt because in the beginning it asks for the partition table type and I chose EFI GPT partition map (Mac i386, some x86_64...). then it showed 'invalid gpt structure'...
maybe I should chose |INTEL| instead...

anywayz, I'm open for further sugestions...

---

### Post by Krytarik on 2011-04-04
> **cerke said:**
> 
maybe testdisk made this confusion with gpt because in the beginning it asks for the partition table type and I chose EFI GPT partition map (Mac i386, some x86_64...). then it showed 'invalid gpt structure'...
maybe I should chose |INTEL| instead...

Yeah, I guess so! I assumed you chose "Intel" there! Since you have a PC, and didn't format the disk with a Mac, isn't it?

---

### Post by oldfred on 2011-04-04
In gparted what do the red exclamation points say is the problem. Click or right click on exclamation point for info.

You may have to run e2fsck on the linux partitions & chkdsk on the windows partition.

From liveCD so everything is unmounted,swap off if necessary, change sda1 to your  other partition sda5 also if it works on sda1.
e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by cerke on 2011-04-04
yeah krytarik, this was my fault. 
the disk was never formatted with a Mac so I should have chosen INTEL instead.

@ oldfred: now that I see what the error was, I'll try to fix it.
I have few options: testdisk, e2fsck and chkdsk. I think I'll start from that and then see if any improvements are shown.

I will post my progress, so hope to return with some good news! :)

---

### Post by cerke on 2011-04-05
and indeed good news I bring!! :)
after doing some changes with testdisk, fdisk and gdisk, and playing a little with exporting and importing partition table.txt files I got this: 
```
**ubuntu@ubuntu:~$ sudo fdisk -lu**

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00009d7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   445990911   222994432   83  Linux
/dev/sda2       445996530   468519659    11261565    7  HPFS/NTFS
/dev/sda3       482287365   488392064     3052350    f  W95 Ext'd (LBA)
/dev/sda5       482287428   488392043     3052308   82  Linux swap / Solaris

**ubuntu@ubuntu:~$ sudo sfdisk -d**
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=445988864, Id=83, bootable
/dev/sda2 : start=445996530, size= 22523130, Id= 7
/dev/sda3 : start=482287365, size=  6104700, Id= f
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=482287428, size=  6104616, Id=82

**ubuntu@ubuntu:~$ sudo parted /dev/sda print**
Model: ATA FUJITSU MHZ2250B (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  228GB  228GB   primary   ext4            boot
 2      228GB   240GB  11.5GB  primary   ntfs
 3      247GB   250GB  3126MB  extended                  lba
 5      247GB   250GB  3126MB  logical   linux-swap(v1)

```finally, Gparted shows the right partitions without any exclamation points:
[http://ubuntuforums.org/attachment.php?attachmentid=188140&stc=1&d=1301999545](http://ubuntuforums.org/attachment.php?attachmentid=188140&stc=1&d=1301999545)

and as an attachment there is my RESULTS.txt .

now the only problem is that when I reboot and try to boot my system it says:
''[B]NTLDR is missing
Press any key to restart[/B]''

I think I saw this NTLDR file in the Windows system files
done some searching about that and few solutions came up.
first, I could copy the ntldr and ntldr.com files from the win xp installation cd.
second, I could try to edit the boot.ini file. maybe the right location of booting isn't set.
third, I could run the win7 install dvd and run the bootrec.exe -> fixboot and fixmbr  commands.

any advices guys, so I don't screw up something again?

(oh, just a note: I don't really care what happens to windows, I just want my ubuntu partition back. so can I boot linux partition without solving this windows problems? maybe try to install grub2 again?)

thanks in advance, and sorry for this looong post. :)

---

### Post by oldfred on 2011-04-05
You cannot read the sda1.

ambivalent result (probably more filesystems on the device, use wipefs(8) to see more details)

This may be a solution, but supposedly the issue was fixed a version or two ago.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

To get the windows repair CD to see your windows install you have to move the boot flag to the windows sda2 partition. Grub does not use a boot flag.

---

