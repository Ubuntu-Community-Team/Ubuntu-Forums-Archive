---
title: "NTLDR is missing"
date: 2009-03-01
forum: General Help
---

### Post by thefonz37 on 2009-03-01
Ok, I have a tricky problem.  I have 2 hard drives - one with WinXP Service pack 3, and one with Intrepid.  Everything was going fine until I got a virus on my WinXP partition.  I used Acronis to reimage the partition and get it working.  Only problem is that somewhere along the line, I screwed up my Linux hard drive and now when I try to boot from it to use Grub and select the OS, I get the message:

NTLDR is missing
Press Ctrl-Alt-Del to reboot

The difficulty here is that I had backed up my files in the Linux partition, so I would like to avoid having to format the hard drive entirely and start over.

I can boot from Windows now, provided I set the bios that way, or I can boot Ubuntu from the install CD, but it won't let me mount the wayward hard drive.

Any suggestions?  I'm a little new to using Linux, so I might not understand everything you say immediately.  Thanks in advance.

---

### Post by damis648 on 2009-03-01
So let me get this strait: When booting from the HD with Ubuntu, you can boot to Ubuntu but not to Windows (NTDLR Error), and when you boot from the other HD you can boot to Windows?

---

### Post by thefonz37 on 2009-03-01
> **damis648 said:**
> So let me get this strait: When booting from the HD with Ubuntu, you can boot to Ubuntu but not to Windows (NTDLR Error), and when you boot from the other HD you can boot to Windows?

I get the NTLDR error when I try to boot from the HD with Ubuntu on it.  When I reset the BIOS, I can boot from the Windows HD.

---

### Post by damis648 on 2009-03-01
> **thefonz37 said:**
> I get the NTLDR error when I try to boot from the HD with Ubuntu on it.  When I reset the BIOS, I can boot from the Windows HD.

Can you boot Ubuntu alright?
If you can, can you post the output of the following commands:
```
cat /boot/grub/menu.lst
```
and also
```
fdisk -l
```
so we may be able to help further. :popcorn:

---

### Post by 73ckn797 on 2009-03-01
Go to Applications/Accessories/Terminal.

Enter:
```
gksudo gedit /boot/grub/menu.lst
```Insert the following"
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```Place this at the very end of the "menu.lst". I assume the partition will be the same if the Windows drive is the first drive. Reboot and see what happens.

If this is already in the "menu.lst" the I would suggest locating "Super Grub Disk". 

You could also boot from the WIndows XP disk, enter recovery mode and type:
```
 fixmbr
```This is only if the grub is not on that drive.

---

### Post by Rallg on 2009-03-01
Do you have a live Linux on an independent USB? If so, boot to it. What does it say about your partitions? In particular, do you have more than one partition claiming to be Windows? If you have only one, does its internal file structure look correct, or are there any re-named files or folders?

Are your partitions where the hard drive boot loader expects them to be? Did you do anything that changed the UUID of a partition, so that it is different from what is in grub menu.lst?

---

### Post by caljohnsmith on 2009-03-01
I think it would help to get a clearer picture of your setup related to booting, so In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by thefonz37 on 2009-03-01
> **damis648 said:**
> Can you boot Ubuntu alright?
If you can, can you post the output of the following commands:
```
cat /boot/grub/menu.lst
```
and also
```
fdisk -l
```
so we may be able to help further. :popcorn:

I can only boot Ubuntu from the CD, not from the partition. Here's what those commands give me:

```
cat: /boot/grub/menu.lst: No such file or directory
```
```
Cannot open /dev/sda
Cannot open /dev/sdb
```

The drive with Ubuntu on it is /dev/sda and I can't seem to mount it, even if I try to force mount.  I tried the command:

```
sudo mount -t ntfs-3g /dev/sda/media/disk -o force
```

As suggested by the help warning and all it gives me is a rundown of the mount command.

Here's my results.txt file:

```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69205244

Partition  Boot         Start           End          Size  Id System

/dev/sda1     ?   218,129,509 1,920,119,918 1,701,990,410   7 HPFS/NTFS
/dev/sda2     ?   729,050,177 1,273,024,900   543,974,724  74 Unknown
/dev/sda4       2,692,939,776 2,692,991,410        51,635   0 Empty

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda2
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xef35ef35

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,296,384   156,296,322   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda: UUID="EA0C770A0C76D155" TYPE="ntfs" 
/dev/sdb1: UUID="EAFC02C2FC0288D1" LABEL="New Volume" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  fe ff ff 0f 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  ff ff ff 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  55 d1 76 0c 0a 77 0c ea  |........U.v..w..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 07 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mp.essed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
```

Hmm...seems like 

```
 => No known boot loader is installed in the MBR of /dev/sda
```

Is likely my problem.  How do I get a boot loader into the MBR if I can't mount the drive?

---

### Post by caljohnsmith on 2009-03-02
Your partition table on the sda 500 GB drive appears to be corrupt. I would suggest using "testdisk" to see if it can recover your valid linux partitions. To use testdisk, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the sda HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions you think are your valid Ubuntu partitions. And lastly, do you remember how many partitions you had on the sda drive, and what each of those partitions were for?

---

### Post by thefonz37 on 2009-03-02
> **caljohnsmith said:**
> Your partition table on the sda 500 GB drive appears to be corrupt. I would suggest using "testdisk" to see if it can recover your valid linux partitions. To use testdisk, how about downloading the [testdisk-6.10.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the sda HDD and then "Proceed", "Intel", "Analyze", "Quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions you think are your valid Ubuntu partitions. And lastly, do you remember how many partitions you had on the sda drive, and what each of those partitions were for?

That took me awhile, I kept hitting Crtl-C to copy and it exited the program!  Doh!

Here's what I  got from the deeper search:
```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
D Linux                    0   1  1 60044 254 63  964622862
D HPFS - NTFS              0   1  2     0 254 63      16001
D HPFS - NTFS              1   1  1 60800 254 63  976751937
D Linux Swap           60045   1  1 60800 254 63   12145077









Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock, 493 GB / 459 GiB
```

For each partition listed, here are the results of P:

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   D Linux                    0   1  1 60044 254 63  964622862
Directory /

drwxr-xr-x     0     0      4096 22-Feb-2009 05:18 .
drwxr-xr-x     0     0      4096 22-Feb-2009 05:18 ..
drwx------     0     0     16384 27-Dec-2008 10:28 lost+found
drwxr-xr-x     0     0      4096 29-Oct-2008 23:12 var
drwxr-xr-x     0     0     12288  1-Mar-2009 19:32 etc
drwxr-xr-x     0     0      4096  1-Mar-2009 18:31 media
lrwxrwxrwx     0     0        11 27-Dec-2008 10:28 cdrom
drwxr-xr-x     0     0      4096 28-Dec-2008 00:44 bin
drwxr-xr-x     0     0      4096 22-Feb-2009 05:19 boot
drwxr-xr-x     0     0      4096 29-Oct-2008 23:04 dev
drwxr-xr-x     0     0      4096 27-Dec-2008 10:34 home
drwxr-xr-x     0     0     12288 22-Feb-2009 05:16 lib
drwxr-xr-x     0     0      4096 28-Dec-2008 04:10 mnt
drwxr-xr-x     0     0      4096 29-Oct-2008 22:53 opt
drwxr-xr-x     0     0      4096 20-Oct-2008 12:27 proc
drwxr-xr-x     0     0      4096  1-Mar-2009 18:01 root
drwxr-xr-x     0     0      4096  1-Mar-2009 18:00 sbin
drwxr-xr-x     0     0      4096 29-Oct-2008 22:53 srv
drwxr-xr-x     0     0      4096 14-Oct-2008 13:02 sys
drwxrwxrwt     0     0      4096  1-Mar-2009 19:32 tmp
drwxr-xr-x     0     0      4096 28-Dec-2008 00:30 usr
lrwxrwxrwx     0     0        33 22-Feb-2009 05:18 initrd.img
lrwxrwxrwx     0     0        30 22-Feb-2009 05:18 vmlinuz
lrwxrwxrwx     0     0        29 28-Dec-2008 00:40 vmlinuz.10197
lrwxrwxrwx     0     0        32 28-Dec-2008 00:40 initrd.img.old
lrwxrwxrwx     0     0        29 28-Dec-2008 00:40 vmlinuz.old

```

The third line from the bottom of that one is highlighted in red.

Second one:

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

   D HPFS - NTFS              0   1  2     0 254 63	 16001



Can't open filesystem. Filesystem seems damaged.
```

3rd:

```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
   D HPFS - NTFS              1   1  1 60800 254 63  976751937
Directory /

dr-xr-xr-x     0     0         0 26-Dec-2008 22:17 .
dr-xr-xr-x     0     0         0 26-Dec-2008 22:17 ..
```

Nothing happens when I hit P on the last one.

To answer the last question - I didn't create any partitions outside of the ones that Ubuntu itself created on that drive, so I'm not really sure what partitions there were before all this happened.

---

### Post by caljohnsmith on 2009-03-02
> **thefonz37 said:**
> 
```
TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB - CHS 60801 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] Linux                    0   1  1 60044 254 63  964622862
[COLOR="Red"]D[/COLOR] HPFS - NTFS              0   1  2     0 254 63      16001
[COLOR="Red"]D[/COLOR] HPFS - NTFS              1   1  1 60800 254 63  976751937
[COLOR="Red"]L[/COLOR] Linux Swap           60045   1  1 60800 254 63   12145077


```

That's great, the testdisk results look really promising; so using your right/left arrow keys, how about marking each partition in the deep search results as I've shown highlighted in red above. Once you are sure the partitions are marked exactly as shown above, press enter to get the next screen, then select "Write". After that reboot your Live CD (it is important to reboot), and please post the output of the following commands:
```
sudo fdisk -lu
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
If the Grub commands above complete successfully, reboot and let me know how far you get. We can work from there.

---

### Post by thefonz37 on 2009-03-02
> **caljohnsmith said:**
> That's great, the testdisk results look really promising; so using your right/left arrow keys, how about marking each partition in the deep search results as I've shown highlighted in red above. Once you are sure the partitions are marked exactly as shown above, press enter to get the next screen, then select "Write". After that reboot your Live CD (it is important to reboot), and please post the output of the following commands:
```
sudo fdisk -lu
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
If the Grub commands above complete successfully, reboot and let me know how far you get. We can work from there.

I got an error on the 2nd grub command:

```
grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 
```

EDIT- I can mount the regular way, though.  Weird.  I'll have to create a 2nd partition on my other drive and copy my files over and reinstall I suppose.

In any event, it looks like things should be ok from here.  Thanks.

---

