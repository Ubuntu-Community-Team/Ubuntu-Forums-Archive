---
title: "Deleted disk?"
date: 2008-12-06
forum: General Help
---

### Post by Scooter74 on 2008-12-06
Here is my first post and I wish it could be happier. I've only been running Ubuntu for a few weeks so I am a Newbie. I had Windows and Ubuntu working correctly with the MBR on the windows HD and Ubuntu on a seperate drive to get the dual boot thing going. Windows crashed (the wife made me use it, I promise) so I recovered it from a third backup drive. Unfortunately now I can't get into Ubuntu. I tried the Super Grub disk but I think I messed it more. I was getting an error 17 when trying to start Ubuntu and an error 15 from within Super GRUB disk. I have now started off the live CD. Here is my fdisk -l output

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaa721644

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0           0           0    0  Empty
Partition 1 does not end on cylinder boundary.

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb02967bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   484183034   242091486    7  HPFS/NTFS
/dev/sdc2       484183035   490223474     3020220    5  Extended
/dev/sdc5       484183098   490223474     3020188+  82  Linux swap / Solaris

sdb1 is obviously the problem. Please help.

---

### Post by cdtech on 2008-12-06
Looks like a corrupt boot sector maybe. Try typing this in a terminal:
```
dd if=/dev/sdb bs=512 count=1 | hd
```
and lets have a look-see.

---

### Post by Scooter74 on 2008-12-06
No luck. Here is the output but the fdisk gives the same output afterwards.

00000000  eb 48 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.H....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  80 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  44 16 72 aa 00 00 80 00  |........D.r.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
1+0 records in
1+0 records out
00000200
512 bytes (512 B) copied, 0.0140451 s, 36.5 kB/s

---

### Post by Scooter74 on 2008-12-06
Sorry CDTech, just read your post properly. This shouldn't fix it but it does give the hard disk read error which I presume was the reason for the error code 17 and 15 previously mentioned.
Thanks.

---

### Post by mdurham on 2008-12-06
> **Scooter74 said:**
> Sorry CDTech, just read your post properly. This shouldn't fix it but it does give the hard disk read error which I presume was the reason for the error code 17 and 15 previously mentioned.
Thanks.
How do you come to that conclusion? I think what you are seeing is an error message string in that sector. It doesn't mean there is an error.

---

### Post by cdtech on 2008-12-06
You should put that in "code" so its more ledgable. But it looks to be a corrupt partition table. You'll notice on mine the type flag is set to "83". Edit your post to put it in a code block.

```
1+0 records in
1+0 records out
512 bytes (512 B) copied, 6.9562e-05 s, 7.4 MB/s
00000000  eb 48 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.H....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb be be 07 b1 04  |...PW...........|
00000020  38 2c 7c 09 75 15 83 c6  10 e2 f5 cd 18 8b 14 8b  |8,|.u...........|
00000030  ee 83 c6 10 49 74 16 38  2c 74 f6 be 10 07 03 02  |....It.8,t......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  f9 16 01 00 00 00 80 01  |................|
000001c0  01 00 **83** fe 3f be 3f 00  00 00 c0 d1 2e 00 00 00  |....?.?.........|
000001d0  01 bf 05 fe ff ff ff d1  2e 00 c7 96 92 0f 00 fe  |................|
000001e0  ff ff 07 fe ff ff c6 68  c1 0f bb dc 5a 0d 00 00  |.......h....Z...|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by Scooter74 on 2008-12-06
Here is a better presentation. I have downloaded Ubuntu Rescue Remix so maybe I can use testdisk???? to sort out my problems. I'm reluctant to try anything that will lose all my data.
Cheers.
```
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000461511 s, 1.1 MB/s
00000000  eb 48 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.H....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  80 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 c0 8e d8 8e d0 bc  |u....Y|..1......|
00000060  00 20 fb a0 40 7c 3c ff  74 02 88 c2 52 be 7f 7d  |. ..@|<.t...R..}|
00000070  e8 34 01 f6 c2 80 74 54  b4 41 bb aa 55 cd 13 5a  |.4....tT.A..U..Z|
00000080  52 72 49 81 fb 55 aa 75  43 a0 41 7c 84 c0 75 05  |RrI..U.uC.A|..u.|
00000090  83 e1 01 74 37 66 8b 4c  10 be 05 7c c6 44 ff 01  |...t7f.L...|.D..|
000000a0  66 8b 1e 44 7c c7 04 10  00 c7 44 02 01 00 66 89  |f..D|.....D...f.|
000000b0  5c 08 c7 44 06 00 70 66  31 c0 89 44 04 66 89 44  |\..D..pf1..D.f.D|
000000c0  0c b4 42 cd 13 72 05 bb  00 70 eb 7d b4 08 cd 13  |..B..r...p.}....|
000000d0  73 0a f6 c2 80 0f 84 ea  00 e9 8d 00 be 05 7c c6  |s.............|.|
000000e0  44 ff 00 66 31 c0 88 f0  40 66 89 44 04 31 d2 88  |D..f1...@f.D.1..|
000000f0  ca c1 e2 02 88 e8 88 f4  40 89 44 08 31 c0 88 d0  |........@.D.1...|
00000100  c0 e8 02 66 89 04 66 a1  44 7c 66 31 d2 66 f7 34  |...f..f.D|f1.f.4|
00000110  88 54 0a 66 31 d2 66 f7  74 04 88 54 0b 89 44 0c  |.T.f1.f.t..T..D.|
00000120  3b 44 08 7d 3c 8a 54 0d  c0 e2 06 8a 4c 0a fe c1  |;D.}<.T.....L...|
00000130  08 d1 8a 6c 0c 5a 8a 74  0b bb 00 70 8e c3 31 db  |...l.Z.t...p..1.|
00000140  b8 01 02 cd 13 72 2a 8c  c3 8e 06 48 7c 60 1e b9  |.....r*....H|`..|
00000150  00 01 8e db 31 f6 31 ff  fc f3 a5 1f 61 ff 26 42  |....1.1.....a.&B|
00000160  7c be 85 7d e8 40 00 eb  0e be 8a 7d e8 38 00 eb  ||..}.@.....}.8..|
00000170  06 be 94 7d e8 30 00 be  99 7d e8 2a 00 eb fe 47  |...}.0...}.*...G|
00000180  52 55 42 20 00 47 65 6f  6d 00 48 61 72 64 20 44  |RUB .Geom.Hard D|
00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  44 16 72 aa 00 00 80 00  |........D.r.....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by cdtech on 2008-12-06
Much better...
The starting byte (66 bytes from the end of the partition table) is correct "80" but the first partition is unallocated (all "0's") and has been corrupt some how, it's also missing partitions 2 and 3 (ie. 1d0, 1e0). I'm not absolutely sure if the "testdisk" will repair the partition table. Even if you edited the partition table to include 2 and 3 and knew the size of the original partition it would be a challenge.
```

00000190  69 73 6b 00 52 65 61 64  00 20 45 72 72 6f 72 00  |isk.Read. Error.|
000001a0  bb 01 00 b4 0e cd 10 ac  3c 00 75 f4 c3 00 00 00  |........<.u.....|
000001b0  00 00 00 00 00 00 00 00  44 16 72 aa 00 00 **80 00**  |........D.r.....|
**000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00**  |................|
*
**000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa**  |..............U.|
00000200
```
Do you know how you formated the drive to begin with?

**UPDATE::.**
> DESCRIPTION
          TestDisk checks and recovers lost partitions
It does say it will, worth a shot........

---

### Post by Scooter74 on 2008-12-06
I can't remember how it was formatted. It was used for windows but then I changed it to a single partition when I installed Ubuntu. I'll give Testdisk a try and see what happens.

---

### Post by Scooter74 on 2008-12-07
Well I've just bitten the proverbial bullet and am doing a re-install now. Testdisk couldn't help me. The good thing about Ubuntu is that I can get the whole thing up an running in only a few hours with all the add-ins I'll ever need. This time I've used the auto partition but without the windows HD installed. I'll sort out the dual boot later.

---

### Post by sandman3838 on 2008-12-07
INTERESTING READ!
fdisk -l 

DO YOU JUST RUN THIS IN TERMINAL?

I DID AND WHAT I GOT BACK WAS:

Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc
Cannot open /dev/sdd

WHAT DID I DO WRONG?

---

### Post by adult swim on 2008-12-07
you are going to need to put sudo in there first to give you permission to do it
```
sudo fdisk -l
```

---

### Post by cdtech on 2008-12-07
> **Scooter74 said:**
> Well I've just bitten the proverbial bullet and am doing a re-install now. Testdisk couldn't help me. The good thing about Ubuntu is that I can get the whole thing up an running in only a few hours with all the add-ins I'll ever need. This time I've used the auto partition but without the windows HD installed. I'll sort out the dual boot later.

Remember after your install, you should backup the sector in case this happens again.
```
dd if=/dev/**sda** of=/home/user/MBR.img bs=512 count=1
```
(Use your own device above)
Then if you need to repair it just do:
```
dd if=/home/user/MBR.img of=/dev/**sda** bs=512 count=1
```

---

### Post by sandman3838 on 2008-12-07
I'M BACK!

USING:
CODE:

sudo fdisk -l

WHAT I GOT BACK WAS THIS - 

      DO YOU SEE ANY ISSUES?

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb329b329

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa411a411

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06e41ad8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       18662   149902483+  83  Linux
/dev/sdc2           18663       19457     6385837+   5  Extended
/dev/sdc5           18663       19457     6385806   82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66305c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS

---

### Post by cdtech on 2008-12-07
I don't see any. What problems are you having?

---

### Post by sandman3838 on 2008-12-07
NO NO its fine!

I just wasn't sure!

It all looked rather messy!

---

