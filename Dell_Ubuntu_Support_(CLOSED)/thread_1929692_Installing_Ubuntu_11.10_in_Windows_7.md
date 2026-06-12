---
title: "Installing Ubuntu 11.10 in Windows 7"
date: 2012-02-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by totalfunky on 2012-02-22
I need to install Ubuntu 11.10 inside Windows 7 on Dell Latitude E6410. I've already downloaded iso image of the same. Could someone please help me out and let me know how I can install the same using USB drive. Till now I've tried following:
1. Created a bootable usb drive and try to install it but couldn't get any option to create a seperate partition for the same. (Though I didn't want to install like this as I want to install inside windows 7 only)
2. Tried with the help of unetbootin-windows-568.exe and used following options 
Distribution : Ubantu Version : 11.10_Live
DiskImage : Path of image ubuntu-11.10-desktop-i386.iso on my local system.
Type : Hard Disk   C:\ (Second time I used USB Drive but it also didn't work)
but after installation when I rebooted the system I got a messge saying "Unable to find a medium containing a live file system". 
 
Please help.
 
-Regards

---

### Post by Inotamira on 2012-02-22
To put it simply, you can't technically install Ubuntu INSIDE windows, only along side. So you would have to either make a separate partition using windows partitioning and then install Ubuntu to that partition (aka dual boot) or, you can use wubi in witch it would behave like a dual boot but it wouldn't require that you made more then one partition.

Personally I suggest the dual boot option as wubi is a little unstable and tends to fall apart

---

### Post by totalfunky on 2012-02-23
Thanks for your reply Inotamira.
Even I think that It's not a good idea to install ubuntu seperately while there is a good option available to install it inside window. In fact I've some bitter experiences of window crash due to installation of other linux flavour (red hat n mandrake). 
But my problem is that the window installer provided by ubuntu, downloads the same iso file on it's own, which I already have. What I want to use the same iso file to install it inside window. How can I do so? Or is there some other way to do the same using USB drive?
-Thanks again for your response.

---

### Post by bcbc on 2012-02-23
Not sure what you want to do ultimately, but for Wubi, if you place wubi.exe and the ISO in the same directory, then wubi will find and use it. It must be the Desktop CD ISO (not the alternate ISO or DVD ISO) and the wubi.exe must be the same release as the ISO. 

Please remove any Ubuntu CD/USBs you have as Wubi also finds those and doesn't install from USBs (except in an exceptional case).

If you want to install a normal dual boot, follow the instructions on [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) (step 2, click USB, then SHOW ME HOW).

---

### Post by totalfunky on 2012-02-23
**_What I want to do:_**
 
I want to install latest version of Ubuntu (11.10) inside windows 7 on my laptop.  
 
 
**_Which iso I'm using:_**
**** 
I've downloaded the corresponding iso from [http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)
using ubuntu-11.10-desktop-i386.iso.torrent
 
**_What I tried:_**
**** 
I've downloaded wubi.exe from [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer) and as per comments given by ***bcbc. ***I put both iso file and wubi.exe in the same folder and when I run wubi I got the attached error.
Would you please let me know that exceptional case where I can use my usb drive for installation.

---

### Post by totalfunky on 2012-02-23
I would also like to mention two more issue which I've faced.
 
**_Issue # 1:_**
**** 
1. Created a bootable usb drive with the help of iso *ubuntu-11.10-desktop-i386.iso *and *Universal-USB-Installer-1.8.8.4.exe *
2. Did Boot laptop thru usb drive. 
3. Choosen try ubuntu from usb (preview option).
4. I got a nice desktop of Ubuntu.
5. On desktop I got an option to install ubuntu as mentioned in 
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) ->4. Install it -> Show me how.
6. During installation I got only 2 options 1. Erase the disk and install Ubuntu and 2. Something else. But I didn't get any *option Install Ubuntu along side Windows 7*. As shown in image 4 in link mentioned in #5.
What I'm missing?? 
 
**_Issue # 2_**
**** 
Tried with the help of unetbootin-windows-568.exe and used following options 
Distribution : Ubantu Version : 11.10_Live
DiskImage : Path of image ubuntu-11.10-desktop-i386.iso on my local system.
Type : Hard Disk C:\ 
but after installation when I rebooted the system I got a messge saying "Unable to find a medium containing a live file system".

---

### Post by CapnKirk on 2012-02-23
I'm not sure what you mean by installing Ubuntu "inside" Windows 7. I run Ubuntu in a VM under Windows 7.

Here is my setup:

E6520 Dell Latitude i7 Quad Core 8GB RAM

It came with Windows 7 preinstalled. I downloaded VMPlayer, copied the Ubuntu iso to the hard drive, and followed [**these instructions**]("http://ubuntuguide.org/wiki/Ubuntu:Oneiric#VMWare").

Works great, although there are little glitches that need fixing. That will depend on your specific setup.

Hope this helps.

---

### Post by bcbc on 2012-02-23
> **totalfunky said:**
> **_What I want to do:_**
 
I want to install latest version of Ubuntu (11.10) inside windows 7 on my laptop.  
 
 
**_Which iso I'm using:_**
**** 
I've downloaded the corresponding iso from [http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)
using ubuntu-11.10-desktop-i386.iso.torrent
 
**_What I tried:_**
**** 
I've downloaded wubi.exe from [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer) and as per comments given by ***bcbc. ***I put both iso file and wubi.exe in the same folder and when I run wubi I got the attached error.
Would you please let me know that exceptional case where I can use my usb drive for installation.

The screenshot you showed is due to this bug: [lpbug]365881[/lpbug]
You can either 'click' through the popups (irritating but it isn't a loop), or remove unnecessary peripherals, mmc readers, usb devices.

The exceptional case for a USB is when the partition is < ~852 MB. Wubi has a size check supposed to exclude DVD ISOs but when you install from USB it copies the whole partition. If it exceeds 900000000 bytes it'll be rejected.

---

### Post by bcbc on 2012-02-23
> **totalfunky said:**
> I would also like to mention two more issue which I've faced.
 
**_Issue # 1:_**
**** 
1. Created a bootable usb drive with the help of iso *ubuntu-11.10-desktop-i386.iso *and *Universal-USB-Installer-1.8.8.4.exe *
2. Did Boot laptop thru usb drive. 
3. Choosen try ubuntu from usb (preview option).
4. I got a nice desktop of Ubuntu.
5. On desktop I got an option to install ubuntu as mentioned in 
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) ->4. Install it -> Show me how.
6. During installation I got only 2 options 1. Erase the disk and install Ubuntu and 2. Something else. But I didn't get any *option Install Ubuntu along side Windows 7*. As shown in image 4 in link mentioned in #5.
What I'm missing?? 
 
**_Issue # 2_**
**** 
Tried with the help of unetbootin-windows-568.exe and used following options 
Distribution : Ubantu Version : 11.10_Live
DiskImage : Path of image ubuntu-11.10-desktop-i386.iso on my local system.
Type : Hard Disk C:\ 
but after installation when I rebooted the system I got a messge saying "Unable to find a medium containing a live file system".

Issue #1: you probably already have 4 primary partitions. The installer cannot install side-by-side with Windows if it is not able to split one of the partitions. And you cannot do this if you already have 4 primary partitions in place (max for MBR partition tables).

Not sure what's you're doing on Issue #2

---

### Post by totalfunky on 2012-02-26
Thanks everybody for their help n support.
 
I decided to go with ***bcbc ***and finally able to run wubi.exe after some irritating popups. Which after a few mins of execution asked me to reboot the system to finish up the ubuntu installation. When I did that I got a message as attached. Though I can see a folder/file in my system at ***C:\ubuntu\install\installation.iso .*** As per the message when I try to run check disk I was unable to do so and my system couldn't boot up not sure why. Somehow I manage to run windows again but unable to run windows.
 
Also ***bcbc ***I've only one partition on my system as C: with around 150 GB free space.
 
Could you please let me know what next I need to do now?
 
-Thanks

---

### Post by bcbc on 2012-02-26
There is some problem that prevents Ubuntu from determining what's on the disk. That would explain why it doesn't detect Windows when you tried to install from a live CD.

Please can you boot that USB again, select "Try Ubuntu" (without installing) and then when you get to the desktop, connect to the internet and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That will provide a bit more information as to what the problem is. Thanks

---

### Post by DeathShot on 2012-02-27
If you have the version of windows that came with your computer then you have more then one partition, they are just hidden.

Personally when I get a new computer I install a fresh copy of windows, you can get a copy from something like the PirateBay and** it will be completely legal so long as you have a valid key which you own**. Lucky for you if you have an OEM computer, you have a key on the side of your desktop or on the bottom of your laptop so just make sure to get the right version of windows. If you do that you can just reformat your PC and make sure that you remove all of the other partitions. Once you do that you can have one partition for windows and install Ubuntu on any of the space you leave over, having them both installed side by side with out any problems. The only down side is that you need to reformat windows.

If you want to truly install it within windows 7, you want a virtual machine. Someone already mentioned VMware Player. It is a free software that lets you configure a virtual machine that runs with in your copy of windows, and it installs just like normal ubuntu. Look at this picture of my desktop:[IMG]http://i40.tinypic.com/8wf7rs.png[/IMG]

As you can see, I am running Windows 7 and on the left I have Firefox with this post open in Windows, and on the right I have VMWare open with multiple vertual machines, the active one being Ubuntu 11.10 with Firefox opened there and my UserCP displaying. This lets me run Ubuntu as if it was a real computer, even in full screen so you can't actually see windows, without having to partition my hard drive or ever actually leave windows. I think this is what you actually want, but I may be wrong.

---

### Post by totalfunky on 2012-03-03
***bcbc ***Thanks for your reply. I followed the instructions and after running the mentioned script got *result.txt* which I'm attaching here.

-Thanks

---

### Post by bcbc on 2012-03-03
The file system and boot sector cannot be determined on /dev/sda1. Do you have disk encryption enabled? 

To make it easier to review:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 2011-12-09
    Boot sector info:   Syslinux looks at sector 7355520 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     7,935,999     7,927,936   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        9846-14FD                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          2

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  cb a3 23 cd 16 67 34 f3  b5 23 2d 06 16 ed 56 0b  |..#..g4..#-...V.|
00000010  f9 a9 e1 4d a3 6a 48 61  65 9e f5 94 b4 e0 90 b7  |...M.jHae.......|
00000020  a5 f4 87 a1 d6 ab 45 b8  98 be 58 4f a7 3d c7 07  |......E...XO.=..|
00000030  7a f6 22 35 e6 9a 34 8a  9a 07 88 cc 84 53 2d 71  |z."5..4......S-q|
00000040  93 e8 85 c2 e8 08 46 2d  c5 a9 91 2f 31 fe 0b 00  |......F-.../1...|
00000050  9c 2c 05 35 87 0f ac ea  f4 4e ac 7b 82 7c 5b 12  |.,.5.....N.{.|[.|
00000060  a1 a6 2a 44 5c f7 05 d2  52 58 bf db d3 81 dc 0c  |..*D\...RX......|
00000070  f8 06 d9 b7 54 19 56 0a  0c f8 9c 6d e8 4b c6 02  |....T.V....m.K..|
00000080  54 fb 15 d9 7f aa 6c 03  9b ad 5a 27 87 29 05 cf  |T.....l...Z'.)..|
00000090  f9 1e 94 46 30 25 4e a1  80 14 65 41 c9 e7 31 a4  |...F0%N...eA..1.|
000000a0  6c 90 03 de c4 64 fc 57  d0 64 32 9b 14 ef 0a 7f  |l....d.W.d2.....|
000000b0  1b 65 dd fa d3 b1 72 63  1c 61 fc 2b 31 44 d2 72  |.e....rc.a.+1D.r|
000000c0  7a ee f0 a6 a7 7f 89 64  be 8c a6 b1 9b 4d e4 08  |z......d.....M..|
000000d0  a1 62 01 da 0f 75 de 1c  54 d1 55 d4 5d ce 6b a3  |.b...u..T.U.].k.|
000000e0  20 ac ab ba 6a eb c1 c2  78 9b 30 c3 08 63 2c 75  | ...j...x.0..c,u|
000000f0  21 f7 81 dc 52 d0 ab d8  6e 61 42 af ae 55 ba 93  |!...R...naB..U..|
00000100  91 15 3d 99 84 a5 98 5e  25 fe 49 cc 1c 5d ad 35  |..=....^%.I..].5|
00000110  c7 5b 25 c8 2b a5 70 a2  29 6c bb c2 67 dd b6 ab  |.[%.+.p.)l..g...|
00000120  24 2d 53 60 06 ed ba f6  c0 38 e5 f0 c3 07 8f 47  |$-S`.....8.....G|
00000130  79 39 66 97 47 a9 92 12  53 47 5f 5f b9 3c 4d b1  |y9f.G...SG__.<M.|
00000140  9a a0 76 13 26 09 08 69  6a cb fe 75 19 8d 32 cd  |..v.&..ij..u..2.|
00000150  15 73 e1 1d 76 87 bd c8  4d b5 64 e7 18 ec 47 35  |.s..v...M.d...G5|
00000160  0e 5e f8 a0 10 7e 46 16  4e 3b 5b 9c 8d 4d 85 fe  |.^...~F.N;[..M..|
00000170  88 d7 f7 0d 90 db a1 f8  3f 90 c5 88 98 b5 ce f6  |........?.......|
00000180  bc 05 94 cd 1d e4 4e a8  59 13 85 09 8a 18 c0 5f  |......N.Y......_|
00000190  28 a7 d3 ca f6 3b db 59  34 3b 6a b2 1f ae 4f bc  |(....;.Y4;j...O.|
000001a0  5b 43 55 db 48 5f 56 b8  a0 cf 14 8e 6d f8 35 8e  |[CU.H_V.....m.5.|
000001b0  bf b1 c2 ca 0a bd 9f d9  13 61 a9 a2 3d 23 40 34  |.........a..=#@4|
000001c0  15 57 a5 c4 d0 6d 07 71  aa 6a 0f 1f 18 13 04 c1  |.W...m.q.j......|
000001d0  65 f7 40 41 24 9a 9d 91  41 f8 88 69 0c 30 56 1e  |e.@A$...A..i.0V.|
000001e0  06 25 9b c7 08 bd e7 41  61 08 16 65 ae 7f de 2b  |.%.....Aa..e...+|
000001f0  04 1c 25 18 0b 7c b8 e0  61 5f 5c 10 77 e4 55 bc  |..%..|..a_\.w.U.|
00000200


=============================== StdErr Messages: ===============================

boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by totalfunky on 2012-03-04
***bcbc*** yes u r rite.. even I doubt the same that coz of that I'm facing this issue. Is there any way to install ubuntu in this scenario?

---

### Post by totalfunky on 2012-03-08
***bcbc*** Is there any way to install ubuntu in case of disk encryption is enabled?

---

### Post by Karlchen on 2012-03-08
Hello, totalfunky.
> **totalfunky said:**
> Is there any way to install ubuntu in case of disk encryption is enabled?In case the MBR and the NTFS filesystem where you want to create a Wubi installation are encrypted you cannot perform a Wubi installation.
The reason is pretty trivial:
The MBR and the encrypted filesystem need to be decrypted at runtime. This can only be done by the Windows software which encrypted them, not by Ubuntu.
If you created a Wubi installation on such an encrypted files system and tried to boot to Ubuntu, Ubuntu would not be able to boot, because it would not be able to find its own filesystem (stored insid \ubuntu\root.disk) on the encrypted disk.

What might be feasible is installing Vmware or Virtualbox and install Ubuntu inside the virtual machine. Yet, I definitely do not know whether VmWare or Virtualbox can be used from an encrypted NTFS partition.

Karl

---

