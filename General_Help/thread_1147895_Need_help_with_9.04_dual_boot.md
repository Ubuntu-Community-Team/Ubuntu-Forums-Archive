---
title: "Need help with 9.04 dual boot"
date: 2009-05-03
forum: General Help
---

### Post by jamesegreen on 2009-05-03
I'm trying to dual boot 9.04 with WinXP.  XP is on a 320GB disk on SATA controller #1 and I'm trying to install 9.04 on a 500GB disk on SATA controller #3 and use the win boot manager.  I installed OK, then wrote the 1st 512 bytes of the /dev/sda1 partition (the 9.04 linux partition) to a ubuntu.bin file like the instructions in several posts and moved it to C:\.  Then added C:\ubuntu.bin="Ubuntu linux" to boot.ini.  But when I select "Ubuntu linux" in the win boot menu, GRUB is printed at the top of the screen and nothing else happens.  Is there some bug in the 512 byte boot segment, or has something changed for 9.04 that makes this not work?

---

### Post by logos34 on 2009-05-03
Why not just boot /dev/sda directly, and [chainload windows on the second hdd]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") instead of the other way around?  It's easier

Did you write grub stage1 to the bootsector of / partition first? i.e.:

sudo grub-install /dev/sda1

*before* you ran the dd copy command for the .bin file?

---

### Post by jamesegreen on 2009-05-04
Thanks for your reply.

1)  I want to use the windows boot loader because to boot my 2nd windows system, Win2K, which is on the 3rd disk drive, I have to unplug the 500GB Seagate with Ubuntu on it, win2K doesn't like 500GB drives.  Only need to do this occasionally, but ...

2) No, I didn't realize that GRUB stage 1 had to be written to the bootsector of partition 1 before I did the dd copy, I thought it was already there from the Ubuntu install??  I'll try this when I get home tonight.

Thanks again for this suggestion, it may fix my problem.  Last night I re-installed Ubuntu 9.04 on my 500GB disk with the other 2 windows disks disconnected, and it boots up and runs with no problem with just that disk plugged in.  So I think I am almost there.

---

### Post by logos34 on 2009-05-04
ok, I usually figure people have a good reason for wanting to use ntldr, but some are unaware you can use grub to chainload windows on a second hard disk, so I thought I'd mention it.

1) since you say it only happens 'occassionally', I'm wondering if the disk spinup times are altering what drives are recognized by the bios in what order.  You might be able to add a delay for certain disks so they are always initialized in a certain sequence.  Then maybe you won't have to resort to unplugging ubuntu to boot win2000  Just a guess...

2) yep, by default grub writes stage1 to the MBR, not /.  You have to manually specify otherwise

hope that helps

good luck

---

### Post by jamesegreen on 2009-05-04
Well, no luck.  I installed 9.04 with only my 500GB Seagate disk plugged in and working (connected to SATA controller 3), and it boots up fine. 

I then reconnected the 2 other Win disks, and 9.04 booted?? I then noticed that somehow the disk boot order in my BIOS had been changed to SATA controller 3 first.  So I changed it back to the order controller 1(XP), 2(Win2K), 3(9.04), like it formerly was.  WinXP then booted up fine.

I then copied the ubuntu.bin file to C:\ that I made with 9.04 booted up after doing the "grub-install /dev/sda1" as root and selected Ubuntu in the Windows boot menu.  But all I get is "GRUB " and a blinking cursor.

I checked the ubuntu.bin file, both the new one and the one I made before, and they are the same, so apparently grub-install didn't change anything??

The file is:

EB  48  90  00  00  00  00  00  00  00  00  00  00  00  00  00 
00  00  00  00  00  00  00  00  00  00  00  00  00  00  00  00 
00  00  00  00  00  00  00  00  00  00  00  00  00  00  00  00 
00  00  00  00  00  00  00  00  00  00  00  00  00  00  03  02 
FF  00  00  80  37  C1  21  00  00  08  FA  90  90  F6  C2  80 
75  02  B2  80  EA  59  7C  00  00  31  C0  8E  D8  8E  D0  BC 
00  20  FB  A0  40  7C  3C  FF  74  02  88  C2  52  BE  7F  7D 
E8  34  01  F6  C2  80  74  54  B4  41  BB  AA  55  CD  13  5A 
52  72  49  81  FB  55  AA  75  43  A0  41  7C  84  C0  75  05 
83  E1  01  74  37  66  8B  4C  10  BE  05  7C  C6  44  FF  01 
66  8B  1E  44  7C  C7  04  10  00  C7  44  02  01  00  66  89 
5C  08  C7  44  06  00  70  66  31  C0  89  44  04  66  89  44 
0C  B4  42  CD  13  72  05  BB  00  70  EB  7D  B4  08  CD  13 
73  0A  F6  C2  80  0F  84  EA  00  E9  8D  00  BE  05  7C  C6 
44  FF  00  66  31  C0  88  F0  40  66  89  44  04  31  D2  88 
CA  C1  E2  02  88  E8  88  F4  40  89  44  08  31  C0  88  D0 
C0  E8  02  66  89  04  66  A1  44  7C  66  31  D2  66  F7  34 
88  54  0A  66  31  D2  66  F7  74  04  88  54  0B  89  44  0C 
3B  44  08  7D  3C  8A  54  0D  C0  E2  06  8A  4C  0A  FE  C1 
08  D1  8A  6C  0C  5A  8A  74  0B  BB  00  70  8E  C3  31  DB 
B8  01  02  CD  13  72  2A  8C  C3  8E  06  48  7C  60  1E  B9 
00  01  8E  DB  31  F6  31  FF  FC  F3  A5  1F  61  FF  26  42 
7C  BE  85  7D  E8  40  00  EB  0E  BE  8A  7D  E8  38  00  EB 
06  BE  94  7D  E8  30  00  BE  99  7D  E8  2A  00  EB  FE  47 
52  55  42  20  00  47  65  6F  6D  00  48  61  72  64  20  44 
69  73  6B  00  52  65  61  64  00  20  45  72  72  6F  72  00 
BB  01  00  B4  0E  CD  10  AC  3C  00  75  F4  C3  00  00  00 
00  00  00  00  00  00  00  00  00  00  00  00  00  00  00  00 
00  00  00  00  00  00  00  00  00  00  00  00  00  00  00  00 
00  00  00  00  00  00  00  00  00  00  00  00  00  00  00  00 
00  00  00  00  00  00  00  00  00  00  00  00  00  00  00  00 
00  00  00  00  00  00  00  00  00  00  00  00  00  00  55  AA 

These are the 512 bytes, which look reasonable.  The text "Grub " starts on the 8th line from the bottom.  Any idea where I went wrong?  Apparently this code segment doesn't point to the 3rd disk?

Thanks for your help.

---

### Post by logos34 on 2009-05-05
hmm.  the previous one should come up all zeroes in the hex editor. I'm probably forgetting something obvious ('ol memory ain't what it used to be).

You might try the grub4dos (grldr) method.  [This page ]("http://users.bigpond.net.au/hermanzone/p9.html")will walk you through it. Doesn't matter where grub stage1/IPL is installed.

Maybe it's an inode issue? (128k vs. the newer 256k on jaunty) dunno.  it's late here, gotta sleep

---

### Post by JK3mp on 2009-05-05
Sounds like a crazy method...why keep win2k?

---

### Post by meierfra. on 2009-05-05
The  normal method to add Ubuntu to the XP boot loader only works if Ubuntu and XP are on the same  hard drive. Since Ubuntu is on a different drive, you have to install Grub in special way:

```
sudo grub
device (hd0) /dev/sda
device (hd2) /dev/sda
root (hd2,0)
setup (hd0,0)
quit
```

This assume that the Ubuntu drive is third in the boot order. If Ubuntu is second, you would have to use "1"'s in place of the "2"'s

Note that you will have to replace ubuntu.bin by the new boot sector after you reinstalled grub.

---

### Post by jamesegreen on 2009-05-05
meierfra,

Thanks loads!!!  Your code worked wonders, and my 9.04 now boots up and runs.  I checked the new file against the old one, and it is almost the same except for a few bytes near the front, so I guess those bytes pointed to the different disk.

But a question, what does your code really do?  Something subtle is happening there that I don't understand.  But it worked, so I am curious why.

Thanks again.

---

