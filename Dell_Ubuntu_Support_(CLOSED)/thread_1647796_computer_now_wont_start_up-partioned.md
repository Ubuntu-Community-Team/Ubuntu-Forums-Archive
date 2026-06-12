---
title: "computer now wont start up-partioned"
date: 2010-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sniper8752 on 2010-12-17
i partioned my hard drive, and i think i deleted my windows os.  i don't see it on my computer.  my computer won't boot the windows 7, but only the ubuntu cd... what do i do?

---

### Post by oldfred on 2010-12-17
Do not touch hard drive. If you write anything into it, you may cause further damage.

Run this script from liveCD that will scan your system. 

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

If partitions are gone, then you can try testdisk which you can also download to the liveCD to try to recover partitions.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by sniper8752 on 2010-12-17
the file was bigger than the allocated amount. what do i do?

---

### Post by sniper8752 on 2010-12-17
here is the file: [http://download732.mediafire.com/fdvt4awas5gg/5xtnxejzvspgnd6/results.txt](http://download732.mediafire.com/fdvt4awas5gg/5xtnxejzvspgnd6/results.txt)

---

### Post by oldfred on 2010-12-17
Thats not results.txt but boot_info_script055.sh. You also just copy & paste the contents of results.txt to a message and then highlight (like copying again) and click on the # in the edit panel at the top of the message to add code tags.

---

### Post by Brvtvs on 2010-12-18
The same thing happened to me, but i freaked out and deleted my windows partition, now I love ubuntu lol

---

### Post by sniper8752 on 2010-12-18
_[U]nvm... here we go..._[/U][]("http://www.mediafire.com/?qn9278t0nadl329")

---

### Post by sniper8752 on 2010-12-18
so why can't i use the windows 7 disk, but can use the ubuntu disk?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

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

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   300,298,239   300,296,192  83 Linux
/dev/sda2         300,300,286   312,580,095    12,279,810   5 Extended
/dev/sda5         300,300,288   312,580,095    12,279,808  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        44C0-E36B                              vfat       New Volume                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        bc921aa8-46e7-4a4d-af76-fc98251cd388   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  9c 9d 24 86 08 9f f5 80  72 87 0d 1b 87 0d 24 13  |..$.....r.....$.|
00000010  e1 a4 8f 8d b5 be ca f8  81 68 80 cc bd b8 fc 8e  |.........h......|
00000020  16 8d 14 42 04 30 06 26  02 38 01 a0 8d a6 98 ec  |...B.0.&.8......|
00000030  1d 7c fe 27 da 5b d5 bd  99 76 8d 3d 71 ed 8d 22  |.|.'.[...v.=q.."|
00000040  ae 48 ee 0e 96 ab bb 30  45 f3 25 9c 2d 58 8f 68  |.H.....0E.%.-X.h|
00000050  7e 57 ff 1c 96 d7 77 46  7f 43 9e 49 e4 e9 23 00  |~W....wF.C.I..#.|
00000060  73 9d d8 c8 4d de 30 65  8b b6 80 00 00 01 1a 12  |s...M.0e........|
00000070  ec f5 ae a9 6b a2 7d d9  bc ef d6 b7 b5 d8 9f e4  |....k.}.........|
00000080  c9 6f 16 31 35 be dd 5d  d9 97 63 a5 28 8a b8 b3  |.o.15..]..c.(...|
00000090  97 84 de 3f 88 93 76 2a  80 a1 30 31 60 67 be 4f  |...?..v*..01`g.O|
000000a0  30 8f ef 7c 3d a5 1d 06  06 dd d7 09 17 21 3d 2c  |0..|=........!=,|
000000b0  a5 f8 85 83 50 3c 8d 43  4e b7 e4 a2 b2 1c 7a 6e  |....P<.CN.....zn|
000000c0  2c d0 e8 bf 48 56 5b 9f  ce 4d 4d ca 50 d8 8e e0  |,...HV[..MM.P...|
000000d0  2a 70 08 9e 73 44 74 5e  80 11 1a d2 36 eb 04 7f  |*p..sDt^....6...|
000000e0  fd f0 c5 37 02 4c 17 63  85 bb 85 c3 ad 31 e3 e8  |...7.L.c.....1..|
000000f0  d9 e4 cf bb 6a bb 46 67  dd 4d 48 c5 81 9f 90 53  |....j.Fg.MH....S|
00000100  a9 c8 31 6d 64 a2 c0 6e  82 51 e9 cc 7b 49 17 6b  |..1md..n.Q..{I.k|
00000110  3a d4 c6 e4 d4 93 03 18  98 9e ca 20 d8 06 64 be  |:.......... ..d.|
00000120  01 a1 35 1c 98 02 45 0e  32 01 0a 09 80 31 db a1  |..5...E.2....1..|
00000130  b3 63 09 68 80 42 05 40  74 03 1e 05 13 86 60 1c  |.c.h.B.@t.....`.|
00000140  1c 06 51 25 e8 24 da 98  4c 48 15 40 66 2b 86 84  |..Q%.$..LH.@f+..|
00000150  0d 1d 8f 68 34 0a 00 a4  86 58 c0 1c 24 98 35 63  |...h4....X..$.5c|
00000160  f4 cd be e1 a5 20 b3 c6  12 e2 f0 6f c5 a1 3b 21  |..... .....o..;!|
00000170  18 0c 27 01 63 2f 9a 22  35 0c 1c f6 39 84 34 94  |..'.c/."5...9.4.|
00000180  9e 12 05 06 7e 4a 09 28  81 00 e8 02 fd f8 14 26  |....~J.(.......&|
00000190  bf e8 26 a4 98 8f d6 af  91 fd a1 21 25 25 92 bd  |..&........!%%..|
000001a0  83 f4 92 6f 47 01 81 35  01 b9 d3 90 5a 09 ce 45  |...oG..5....Z..E|
000001b0  86 ad 09 51 f1 78 23 94  3b 7f 79 88 26 02 00 fe  |...Q.x#.;.y.&...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 bb 00 00 00  |...........`....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by oldfred on 2010-12-18
Just wanted to check that the partitions were not there but not showing in something.

The only alternative is testdisk, but since it is likely you overwrote some of the windows code, I am not hopeful that you can recover a working system. You should get the partition back and then may be able to copy your data. If that does not work testdisk also has photorec that scans drive for files and copies to another drive.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

You want to see if testdisk can find the original NTFS partition and let you restore it.

---

### Post by sniper8752 on 2010-12-18
i did format the hard drive.  i do not really understand these instructions: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step).  i don't know how to install the software.  i extracted the testdisk file, and went into win, but don't see an .exe.  its in dos, but it won't run.  i didn't also install ubuntu actually.

and here is what i get when i do the gnu parted tutorial: _[http://www.mediafire.com/imageview.php?quickkey=p5tri8y8dk83373&thumb=4](http://www.mediafire.com/imageview.php?quickkey=p5tri8y8dk83373&thumb=4)_ (followed tutorial on [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery))  what does it mean that it is parted now?

---

### Post by oldfred on 2010-12-18
If you are running parted, you have to know the exact start and end locations on the drive. IF you have saved that info we could use it but most do not. Testdisk is your best alternative.

You have to use the liveCD of Ubuntu or you can use just about any other Linux based rescue type CD.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by sniper8752 on 2010-12-18
i couldn't find  System>Administration>Software Sources>Ubuntu Software. i have v. 10.10
and which one do i want to download here: [http://www.cgsecurity.org/wiki/TestDisk_Download?](http://www.cgsecurity.org/wiki/TestDisk_Download?) and how do i actually open and run testdisk then?

---

### Post by oldfred on 2010-12-18
I think in Maverick the software sources is System, Administration, Update Manager, settings button on lower left.

I do not know how to run it from windows, but they should have instructions on their site.

---

### Post by sniper8752 on 2010-12-18
well wouldn't i want a linux since it says on the results one that this is a linux platform?  and i tried windows, but i don't think this os likes the .exe... does it use something else to install the file?

---

### Post by oldfred on 2010-12-18
If you are using the liveCD you cannot run windows .exe programs.

Well you cannot run windows programs in Linux unless you have wine installed and then they all do not always work well.

Just download from the repository using Synaptic package manager.

---

### Post by sniper8752 on 2010-12-18
so here is where i am at... [here]("http://www.mediafire.com/imageview.php?quickkey=65y56iz1so0liir&thumb=4") are my sectors. could it be the dell utility since it has to do with the bios? do i write this to the drive?  i don't think that is it though because the dell logo shows when the computer starts, and i can access the bios.... when installing ubuntu and viewing the devices available, i see the fat32 and the swap.

---

### Post by gbrainin on 2010-12-19
It looks to me like a) you somehow deleted the MBR (Master Boot Record) on the hard drive, and b) you still have your windows partition in place.

You might want to check with someone more experienced with windows than I am, but I'm thinking that it might help (and wouldn't make things worse) to just restore the MBR.  Which is done with the following command _in windows_:```
FDISK /MBR
```
On further research, I'm not sure that command still works in Windows 7.  You may need to use a slightly different sequence, as explained here: [http://www.ehow.com/how_4836283_repair-mbr-windows.html]("http://www.ehow.com/how_4836283_repair-mbr-windows.html")

---

### Post by oldfred on 2010-12-19
The MBR is also missing but the NTFS partition was overwritten. You will not be able to recvoer a bootable windows but may bring it back enough that you can copy your files. If your Linux install corrputed the file table the only way to get data back would be to use photorec which is on the testdisk site.

Recovering the NTFS partition will destroy the current install of Ubuntu but I assume that has nothing of value.

---

### Post by sniper8752 on 2010-12-19
ok, its ok if i don't get my original windows back... i have all my files backed up anyway... so how do i re-install windows?  and the link didn't work b/c the startup doesn't recognize windows 7.  how do i  Recover the NTFS partition?

and why do we talk about windows, when i can't even load it? lol im just a little confused about that.

---

### Post by sniper8752 on 2010-12-19
i am trying this, but it did not recover too many files since i formated my hard drive... [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/).  i tried changing the boot sequence to usb (after completing the tutorial), then cd, then internal, and got the error "invalid system disk" while i had the windows 7 in.  i guess this tutorial does not work for me then? i even tried rearranging the boot sequence, and it did nothing for me.  i also tried what they said to do at the end of the tutorial, but i guess the system files were deleted, henceforth, they were not copied to my external hard drive.  i will try to copy and paste my dad's xp system (windows) files to my usb external hard drive, and run them from there... do you think that will work?[URL="http://www.psychocats.net/ubuntucat/recoverdeletedfiles/"]
[/URL]

---

### Post by oldfred on 2010-12-19
If we do not have to worry about files, then we just need to reinstall. I looks like nothing of value install or format wise is on drive, so I would totally start over.

I would make a NTFS primary partition for windows with the boot flag. I would also make another NTFS partition for any data you might want to share between windows and Linux.

Then I would make an extended partition and install logical partitions for Ubuntu.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Then install windows to the first partition. Then install Ubuntu using manual install so you can choose the partitions you have already made.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by sniper8752 on 2010-12-19
[http://www.mediafire.com/imageview.php?quickkey=grjpib8v8ga77h4&thumb=4](http://www.mediafire.com/imageview.php?quickkey=grjpib8v8ga77h4&thumb=4)

so is this right? will i have the windows drive (the first one) then the linux os (the second one)?  and will there be enough room to install the oss in there?

and is a GiB a gigabyte (gb)?

---

### Post by oldfred on 2010-12-19
I think you have to erase those partitions and totally start over. You have to decide how large you want windows NTFS, a NTFS shared data and how much for Ubuntu.

---

### Post by sniper8752 on 2010-12-19
well i am going to be using windows 7 for most of the time, so lets just say for now, 100gb for the windows 7, then 50 for the ubuntu partition.  this can be changed later if needed, right?

---

### Post by oldfred on 2010-12-19
That would work. Sometimes it is not so easy to move partitions around as it depends on where a partition is and where the space is. If not near each other it can be a task to move partitions around.

I might make windows 70 or 80GB in a primary NTFS partition with the boot flag, but then create another NTFS partition for data fo rthe 20 or 30GB, so the total windows is the same, just split. Then you do not have to write shared data into the system partitions. Windows can be sensitive to too much writing from another system. Windows will see it as a C: and a D:.

---

