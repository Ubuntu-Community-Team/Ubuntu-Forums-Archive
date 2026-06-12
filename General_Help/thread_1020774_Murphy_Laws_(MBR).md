---
title: "Murphy Laws (MBR)"
date: 2008-12-24
forum: General Help
---

### Post by Corbin on 2008-12-24
Alrighty, i will start from the beginning. 

I needed to boot into ubuntu for something real fast. So i pulled out one of my bootable CDs i had laying around and poped it in. 

I waited for it boot up and load, but eventually it was just hanging on loading some graphic drivers. So i i didn't feel like messing with it (because it was an older version and because i think i knew what the prob was.) (raid).

So, decided to boot back into windows; but OOPS my raid configuration SOMEHOW got messed up... This has only happened ONCE before so i knew how to fix it. (delete the array and then recreate it) WITHOUT DELETING THE MBR. 

But you see... i was in a fit of rage at the time and was now not reading the stupid questions; but those one of those "stupid little questions" asked if (keep MBR or not to keep the MBR)........ need i say more??

But that wouldn't be so bad... if was wasn't running raid 0 and on windows x64.....

So basically... i am at a lost as how to BUILD/MAKE a new MBR.... (not repairing it). ~ because there is nothing TOO repair.. 


All in all i REALLY am at a loss... (ANY HELP WOULD BE AWESOME).

-Thanks much......

---

### Post by caljohnsmith on 2008-12-24
So do you have a Windows MBR or are you using Grub? In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup.

---

### Post by Corbin on 2008-12-24
NO, i do not have ubuntu Installed.. 
(all windows.) -So no, not using grub or lilo or anything... 
(been out of the Linux scene for a little while now.


I will download the latest ubuntu live CD and give what you said a run.

Because i have been out of the linux scene for so long... this may sound like a stupid question... but... how does ubuntu do with RAID0 set up?

-Thanks.

---

### Post by Corbin on 2008-12-24
Alrighty... i got the newest version of ubuntu up and running off the live CD and i did what you said.

Windows is installed in the MBR of /dev/sda
No boot loader is installed in the MBR of /dev/sdb
No boot loader is installed in the MBR of /dev/sdc
No known boot loader is installed in the MBR of /dev/sdd

sda1:
    File system:  
    Boot sector  type:  No Boot Loader
    Mounting failed:  
mount: you must specify the filesystem type


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x29e529e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  2499971039  1249985488+   7  HPFS/NTFS

/dev/sda1: unknown volume type
Warning: partition 1 extends past end of disk


Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000


/dev/sda1: unknown volume type
Warning: partition 1 extends past end of disk

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.


Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000


/dev/sda1: unknown volume type
Warning: partition 1 extends past end of disk

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdc: unrecognized partition table type

sfdisk: no partition table present.


Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000


/dev/sda1: unknown volume type
Warning: partition 1 extends past end of disk

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type

sfdisk: no partition table present.

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdc: unrecognized partition table type

sfdisk: no partition table present.

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdd: unrecognized partition table type

sfdisk: no partition table present.

/dev/loop0: TYPE="squashfs" 

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

StdErr Messages 

Unknown MBR on /dev/sdd

00000000  01 02 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000010  1d 97 83 ac 7f 01 00 00  10 62 00 00 00 00 00 00  |.........b......|
00000020  88 00 00 00 01 00 04 90  48 00 00 00 58 00 00 00  |........H...X...|
00000030  00 00 00 00 14 00 00 00  02 00 34 00 02 00 00 00  |..........4.....|
00000040  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000050  20 00 00 00 20 02 00 00  00 00 14 00 ff 01 1f 00  | ... ...........|
00000060  01 01 00 00 00 00 00 05  12 00 00 00 01 02 00 00  |................|
00000070  00 00 00 05 20 00 00 00  20 02 00 00 01 05 00 00  |.... ... .......|
00000080  00 00 00 05 15 00 00 00  b3 ac e3 d8 98 84 73 ea  |..............s.|
00000090  a3 9e f4 88 01 02 00 00  00 00 00 00 00 00 00 00  |................|
000000a0  bc c9 12 14 80 01 00 00  a0 62 00 00 00 00 00 00  |.........b......|
000000b0  14 01 00 00 01 00 04 80  c8 00 00 00 e4 00 00 00  |................|
000000c0  00 00 00 00 14 00 00 00  02 00 b4 00 07 00 00 00  |................|
000000d0  00 03 14 00 ff 01 1f 00  01 01 00 00 00 00 00 05  |................|
000000e0  12 00 00 00 00 03 18 00  ff 01 1f 00 01 02 00 00  |................|
000000f0  00 00 00 05 20 00 00 00  20 02 00 00 00 00 24 00  |.... ... .....$.|
00000100  ff 01 1f 00 01 05 00 00  00 00 00 05 15 00 00 00  |................|
00000110  b3 ac e3 d8 98 84 73 ea  a3 9e f4 88 f4 01 00 00  |......s.........|
00000120  00 0b 14 00 00 00 00 10  01 01 00 00 00 00 00 03  |................|
00000130  00 00 00 00 00 03 18 00  bf 01 13 00 01 02 00 00  |................|
00000140  00 00 00 05 20 00 00 00  23 02 00 00 00 03 18 00  |.... ...#.......|
00000150  a9 00 12 00 01 02 00 00  00 00 00 05 20 00 00 00  |............ ...|
00000160  21 02 00 00 00 02 18 00  16 01 00 00 01 02 00 00  |!...............|
00000170  00 00 00 05 20 00 00 00  21 02 00 00 01 05 00 00  |.... ...!.......|
00000180  00 00 00 05 15 00 00 00  b3 ac e3 d8 98 84 73 ea  |..............s.|
00000190  a3 9e f4 88 f4 01 00 00  01 05 00 00 00 00 00 05  |................|
000001a0  15 00 00 00 b3 ac e3 d8  98 84 73 ea a3 9e f4 88  |..........s.....|
000001b0  01 02 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  0e e5 49 9b 81 01 00 00  c0 63 00 00 00 00 00 00  |..I......c......|
000001d0  e8 00 00 00 01 00 04 80  9c 00 00 00 b8 00 00 00  |................|
000001e0  00 00 00 00 14 00 00 00  02 00 88 00 05 00 00 00  |................|
000001f0  00 00 14 00 ff 01 1f 00  01 01 00 00 00 00 00 05  |................|
00000200

Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdc doesn't contain a valid partition table
Disk /dev/sdd doesn't contain a valid partition table




(More info about my system)

Runing Windows Xp pro x64
320 gig hard drive (x4) in Raid 0 (on-board raid controler chip).
4 gigs of ram. 
AMD 6000+ 3.0 dual core

---

### Post by caljohnsmith on 2008-12-24
Do you have your Windows Install CD? If you do, can it deal with your RAID setup OK? If so, I would boot that, go to the "recovery console" and run:
```
fixmbr
```
If for some reason that doesn't work because of your RAID configuration, you could instead open a terminal in Ubuntu (Applications > Accessories > Terminal) and do:
```
sudo lilo -M  /dev/sda mbr
```
If that command doesn't give you an error, reboot, and let me know what happens when you try to boot your RAID array. We can work from there.

---

### Post by Corbin on 2008-12-24
No you see that's the prob. 
I can't repair it using windows stuff because it repairs a broken one... and the thing is. is that mine is not "broken" it is up and up gone/deleted/fried/ said bye bye..... 

But I tried what you said and and it gave me no errors. So i rebooted
and instead of saying NO OS found, it is saying 
No boot-able partition (or something along those lines). + the error refreshes about ever 2 seconds or so...

Hey, i really appreciate the help man... 
(there is some REALLY important stuff on those drive I need). (about 600 gigs of important stuff).....



P.S.- If worse comes to worse I wont mind wiping it and starting over (as long as i get get ONE FOLDER off these drives (the C:/Stuff folder has EVERYTHING i need in it). 

^But i hope i wont have too....



Thanks again.

---

### Post by caljohnsmith on 2008-12-24
OK, from your Ubuntu CD, how about posting the output of:
```

sudo hexdump -n 512 -Cv /dev/sda
sudo hexdump -n 512 -Cv /dev/sdb
```
Next try:
```
sudo lilo -M  /dev/sdb mbr
```
Reboot, and let me know what happens, particularly what error you might get if it is different than the "no bootable partition" error.

---

### Post by Corbin on 2008-12-24
With the      sudo hexdump -n 512 -Cv /dev/sda
ubuntu@ubuntu:~$ sudo hexdump -n 512 -Cv /dev/sda
00000000  fa eb 31 12 00 00 4c 49  4c 4f 16 08 10 00 01 00  |..1...LILO......|
00000010  00 7c 00 00 00 00 00 00  00 00 00 00 5e ac 08 c0  |.|..........^...|
00000020  74 09 b4 0e bb 07 00 cd  10 eb f2 b9 13 00 b4 86  |t...............|
00000030  cd 15 cd 18 31 c0 8e d0  bc 00 7c fb 89 e1 06 53  |....1.....|....S|
00000040  56 52 89 ce fc 8e d8 8e  c0 bf 00 06 b9 00 01 f3  |VR..............|
00000050  a5 ea 56 06 00 00 60 b8  00 12 b3 36 cd 10 61 66  |..V...`....6..af|
00000060  8b 3e b8 07 66 09 ff 74  1b b4 08 b2 80 cd 13 0f  |.>..f..t........|
00000070  b6 ca 92 ba 80 00 e8 9a  00 66 3b 3e b8 7d 74 04  |.........f;>.}t.|
00000080  42 e2 f3 92 be be 07 b9  04 00 f6 04 80 89 f5 78  |B..............x|
00000090  33 83 c6 10 e2 f4 e8 83  ff 4e 6f 20 70 61 72 74  |3........No part|
000000a0  69 74 69 6f 6e 20 61 63  74 69 76 65 0d 0a 00 f6  |ition active....|
000000b0  04 80 79 10 e8 65 ff 49  6e 76 61 6c 69 64 20 50  |..y..e.Invalid P|
000000c0  54 0d 0a 00 83 c6 10 e2  e6 89 ee 66 8b 44 08 66  |T..........f.D.f|
000000d0  a3 14 06 e8 3d 00 81 3e  fe 7d 55 aa 75 11 31 c0  |....=..>.}U.u.1.|
000000e0  58 3c fe 75 06 88 d4 5e  5b 07 92 ff 2e 10 06 e8  |X<.u...^[.......|
000000f0  2a ff 4e 6f 20 62 6f 6f  74 20 73 69 67 6e 61 74  |*.No boot signat|
00000100  75 72 65 20 69 6e 20 70  61 72 74 69 74 69 6f 6e  |ure in partition|
00000110  0d 0a 00 60 bd 0c 00 be  0c 06 bb aa 55 b4 41 cd  |...`........U.A.|
00000120  13 72 0f 81 fb 55 aa 75  09 f6 c1 01 74 04 b4 42  |.r...U.u....t..B|
00000130  eb 3f 52 b4 08 cd 13 72  43 51 c0 e9 06 86 e9 89  |.?R....rCQ......|
00000140  cf 59 c1 ea 08 92 40 83  e1 3f f7 e1 93 a1 14 06  |.Y....@..?......|
00000150  8b 16 16 06 39 da 73 22  f7 f3 39 f8 77 1c c0 e4  |....9.s"..9.w...|
00000160  06 86 e0 92 f6 f1 08 e2  89 d1 41 5a 88 c6 b8 01  |..........AZ....|
00000170  02 c4 5c 04 cd 13 72 05  61 c3 b4 40 5a 4d 74 06  |..\...r.a..@ZMt.|
00000180  30 e4 cd 13 eb 91 e8 93  fe 44 69 73 6b 20 72 65  |0........Disk re|
00000190  61 64 20 65 72 72 6f 72  0d 0a 00 00 00 00 00 00  |ad error........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 44 63  e5 29 e5 29 00 00 80 01  |......Dc.).)....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 a1 87 02 95 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
ubuntu@ubuntu:~$ 






And with the       sudo hexdump -n 512 -Cv /dev/sdb
ubuntu@ubuntu:~$ sudo hexdump -n 512 -Cv /dev/sdb
00000000  00 00 00 00 14 00 00 00  02 00 00 01 02 00 00 00  |................|
00000010  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000020  20 00 00 00 20 02 00 00  00 00 24 00 ff 01 1f 00  | ... .....$.....|
00000030  01 05 00 00 00 00 00 05  15 00 00 00 b3 ac e3 d8  |................|
00000040  98 84 73 ea a3 9e f4 88  f4 01 00 00 00 00 00 00  |..s.............|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  30 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |0...............|
00000070  d8 ad 0a 00 00 00 00 00  40 00 00 00 82 00 00 00  |........@.......|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  f8 84 f7 7f ff 07 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  58 f2 fd ff ff 07 00 00  a4 02 00 00 00 00 00 00  |X...............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  2b 00 2c 00 00 00 00 00  50 af 0a 00 00 00 00 00  |+.,.....P.......|
000000f0  82 51 08 00 01 00 00 00  00 00 00 00 00 00 00 00  |.Q..............|
00000100  00 00 00 00 00 00 00 00  01 05 00 00 00 00 00 05  |................|
00000110  15 00 00 00 b3 ac e3 d8  98 84 73 ea a3 9e f4 88  |..........s.....|
00000120  f4 01 00 00 01 05 00 00  00 00 00 05 15 00 00 00  |................|
00000130  b3 ac e3 d8 98 84 73 ea  a3 9e f4 88 01 02 00 00  |......s.........|
00000140  8c fe f4 10 05 03 00 00  40 63 02 00 00 00 00 00  |........@c......|
00000150  60 01 00 00 01 00 04 80  14 01 00 00 30 01 00 00  |`...........0...|
00000160  00 00 00 00 14 00 00 00  02 00 00 01 02 00 00 00  |................|
00000170  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000180  20 00 00 00 20 02 00 00  00 00 24 00 ff 01 1f 00  | ... .....$.....|
00000190  01 05 00 00 00 00 00 05  15 00 00 00 b3 ac e3 d8  |................|
000001a0  98 84 73 ea a3 9e f4 88  f4 01 00 00 00 00 00 00  |..s.............|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  30 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |0...............|
000001d0  d8 ad 0a 00 00 00 00 00  40 00 00 00 4e 00 00 00  |........@...N...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 ff 07 00 00  02 00 00 00 00 00 00 00  |................|
00000200
ubuntu@ubuntu:~$ 


And with sudo lilo -M  /dev/sdb mbr
^ I got no errors upon entering.... (Now i will restart and let you know.)

---

### Post by Corbin on 2008-12-24
Nope same error as before... But to be more precise it is "No boot signature in partition"

---

### Post by caljohnsmith on 2008-12-24
So your sda drive definitely has a Windows type MBR now, and your sdb drive should since you ran that last lilo command; your sdb drive doesn't have a valid MBR signature though, and your RAID array obviously complicates the booting process. How did you originally install Windows to your RAID? Did you take any special steps to install a different MBR than the usual Windows MBR? Have you ever had to fix the MBR before, and if so, what did you do?

---

### Post by Corbin on 2008-12-24
Yea, the raid0 really does not help the situation... 

The way I installed windows was the way I always do it...

Pop in the CD (xp) press f6 to load the raid/sata drivers and then install windows....


No, i have never messed up my MBR before.... (at least not on this comp.)

Do you know of anything that can scan the hard drive(s) and just build a new MBR.... or anything along those lines...


-Thanks again man...

---

### Post by caljohnsmith on 2008-12-24
> **Corbin said:**
> Yea, the raid0 really does not help the situation... 

The way I installed windows was the way I always do it...

Pop in the CD (xp) press f6 to load the raid/sata drivers and then install windows....


No, i have never messed up my MBR before.... (at least not on this comp.)

Do you know of anything that can scan the hard drive(s) and just build a new MBR.... or anything along those lines...


-Thanks again man...
As far as rebuilding the MBR, that's actually what the "fixmbr" command does that you all ready ran. You might want to keep in mind that all the Windows MBR does on start up is to look in the MBR partition table, find which primary partition is marked bootable, and then the Windows MBR boots the boot sector (the first sector) of that partition. So the only thing that can really be configured is which partition has the boot flag set, and according to the results you posted in your post #4, the sda1 Windows partition is marked bootable like it should be. If you want to try to use Ubuntu to mount the Windows RAID partition in order to access your files, you might want to look into the software package called "mdadm". Another idea that's a bit of a long shot is you could download the "[Super Grub Disk]("http://www.supergrubdisk.org")", because you could use it to try and boot the Windows partition directly; I don't think there's a big chance of it working, but it couldn't hurt to try, and it's a small and quick download anyway. Considering I don't have much experience with RAID, I unfortunately don't think I can help much more. Good luck though, and by the way, Merry Christmas. :)

---

### Post by Corbin on 2008-12-24
Yea, i just tried a few of the "super grub disk" options; but nothing.... 

Now you mentioned this mdadm thing... I started to look into this, and from what I have read, it seems like a viable options.. 


You think that is the best way to retrieve that data off the hard drives?

---

### Post by Herman on 2008-12-25
:) I don't know much about RAID arrays either, except I try to keep away from them.

I just want to put forward the suggestion that you try to boot with an NTLDR boot CD, instead of Super Grub Disk, because the NTLDR CD can actually boot Windows for you, as opposed to just chainloading the boot sector. 
That bypasses the MBR, the boot sector and the three main Windows booting files, NTLDR, NTdetect.com and boot.ini, because is uses copies of those files in the CD itself. 
You can download one from [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").

I don't know if that'll be any help if you have deleted your partition table though. It wouldn't hurt to give it a spin anyway and see what happens.

Windows 'fixmbr' doesn't fix the partition table, it only replaces the bootloader code area of the MBR.
If you need to fix the partition table, the best program I know of for that is [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), (installable in Ubuntu). I don't know how TestDisk will work if you have RAID though. Some more research about that would be required.
EDIT: It appears there is a good chance that TestDisk can fix it for you,
From their home page:
> TestDisk can **find lost partitions** for all of these file systems: 
 
[LIST]
[*]BeFS ( BeOS )
[*]BSD disklabel ( FreeBSD/OpenBSD/NetBSD )
[*]CramFS, Compressed File System
[*]DOS/Windows FAT12, FAT16 and FAT32
[*]HFS, HFS+ and HFSX, Hierarchical File System
[*]JFS, IBM's Journaled File System
[*]Linux ext2 and ext3
[*]Linux LUKS encrypted partition
[*]Linux RAID md 0.9/1.0/1.1/1.2
[LIST]
[*]**RAID 1: mirroring **
[*]RAID 4: striped array with parity device
[*]RAID 5: striped array with distributed parity information
[*]RAID 6: striped array with distributed dual redundancy information
[/LIST]
 
[*]Linux Swap (versions 1 and 2)
[*]LVM and LVM2, Linux Logical Volume Manager
[*]Mac partition map
[*]Novell Storage Services NSS
[*]NTFS ( Windows NT/2000/XP/2003/Vista/2008 )
[*]ReiserFS 3.5, 3.6 and 4
[*]Sun Solaris i386 disklabel
[*]Unix File System UFS and UFS2 (Sun/BSD/...)
[*]XFS, SGI's Journaled File System
[/LIST]
I'm still not too sure though, it says 'Linux RAID', your kind of RAID might be different, especially if it was set up by Windows. Maybe you need some kind of proprietary utility?
$$$

---

### Post by Corbin on 2008-12-25
Ahh thanks for ALL the help guys I really appreciate it! 

Hey, Herman i tried doing what you suggested about the NTLDR boot CD.
and it didn't really get me any further then some of the other things i tired.... (but it was worth a try).

Also^^ I started to look into the whole "TestDisk" thing. and it looks interesting but a bit confusing in some areas.... The thing i'm not sure about. Is that people are referring to some raids as "windows" RAID... When I didn;t really do it though windows... (I have an on-board raid controller card). Or am I mistaken; and that is still considered a "windows" RAID even though your using an on-board raid controller card.... (the Board is a GA-MA69GM-s2h if it helps).  

ALSO, i am running low on time and patients... So i might just bite the bullet and mount the drives and grab my ONE (600 gig) folder off.... Then wipe the drives and start over.... 
^^^^^^^^ Does anyone know of a good walk though for that......
Im running RAID0 with 4 drives (350 gigs a piece). 




PS. Merry Christmas ALL!!!!!!!!! Even when we hit bumps (or man holes), in the road as we go.

---

### Post by Corbin on 2008-12-27
Bump

For any good walk troughs on either mounting your raid drives to retrieve files off it... 

Or 

Data recovery off of raid drives... (just need ONE file off them). 


-Thanks again.

---

### Post by neur0 on 2008-12-27
I'm not sure if you tried it, but
```
fixboot
```

writes a new boot sector

(from the windows recovery console)

---

### Post by Corbin on 2008-12-27
Well... Yes and No.....

The problem is I am unable to GET TO the windows recovery console.... 
I have no idea why... I have seen the options MANY MANY MANY MANY times before... But for some reason when I stick in the CD, it does not give me an options to hit "R" (to get into the recovery console). 

I assumed it was because the MBR was not damaged" but deleted... So it did not even scene a windows installation. Thus not allowing me an options to use the recovery consul... (Or was I wrong). 

I have tried a numerous amount of floppies but non really did the trick... 
I think the windows recovery consul would be the way to go because it reads my RAID drivers (F6) in the very beginning of the install.....

---

