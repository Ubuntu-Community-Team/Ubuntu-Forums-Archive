---
title: "DVD Burning Issues"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Bender NZ on 2005-10-28
Hi,

I have been trying all night to figure out DVD burning in Ubuntu.

Burning CD's is fine - but burning DVD's appears to be successful, but then I cannot read the DVD afterwards.

Here's what I did:

Loaded blank 4x DVD-R, opened k3b (also tried graveman and the nautilus burner). Dragged files on and burned them as a data DVD.

All appeared to burn okay, and when I originally inserted the blank DVD it was picked up happily and I was asked if I would like to burn a new DVD and so on.

Once burning is complete the DVD is ejected, and I put it back in again and it didn't mount, so I tried mounting it manually from the command line.

Here's the output of dmesg | tail

```
bender@radiate:~$ dmesg | tail
[  625.793754] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[  625.793761] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[  625.793766] ide: failed opcode was: unknown
[  625.793771] end_request: I/O error, dev hdc, sector 64
[  625.794542] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[  653.305994] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[  653.306002] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[  653.306007] ide: failed opcode was: unknown
[  653.306012] end_request: I/O error, dev hdc, sector 64
[  653.306777] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

```

I've finalised the DVDs (have attempted 7) so I'm stumped as to what the problem is.

Relevant details:
AMD Turion (64bit)
Ubuntu Breezy (amd64 version)
Asus A6000U laptop (has a builtin dual layer DVD burner so presumably this is an Asus burner - shows up as TSSCorp)

Let me know if you need more information.

As above CD's burn fine - just DVD's are giving me headaches.

---

### Post by Remmelas on 2005-10-28
I've had this occur with media my burner doesn't like, and usually resolved by slowing down the burn rate.  Doesn't mean it will help you but worth a shot.

---

### Post by Bender NZ on 2005-10-28
Hrm yeah I thought about that but it's the same pack of DVD's as I was burning successfully in Windows XP with :(

Might try a slower burn rate though - but the discs are reported as successfully burnt, just can't be read again after :/

---

### Post by Remmelas on 2005-10-28
are you mastering to an ISO image first?  If so, mount the iso image on a loopback first and make sure it's readable.  If you are burning through k3b and mastering through it as well, i'm not too sure, except for maybe the basic stuff like, make sure dma is turned on for your burner, etc.  and, maybe, make sure that you aren't using your pc for any other file io intensive tasks during the burn, i've also seen the problem if the burn relies too heavily on buffer underrun protection schemes on -R type media.

---

### Post by Bender NZ on 2005-10-28
I was burning straight from the HDD before - just tried making an ISO first and it worked!

Cheers for the help.

DMA is on btw for the hdd and dvd so I'd have thought burning from disk should work - but then again it is a laptop so perhaps it's not a good idea to burn straight from disk with slow laptop hdd's.

---

### Post by Remmelas on 2005-10-29
[QUOTE=Bender NZ]I was burning straight from the HDD before - just tried making an ISO first and it worked!

Cheers for the help.

DMA is on btw for the hdd and dvd so I'd have thought burning from disk should work - but then again it is a laptop so perhaps it's not a good idea to burn straight from disk with slow laptop hdd's.[/QUOTE]
not even so much the slower hdd is the problem, but most laptops use a single ide channel for the hdd and the cdrom(or at least the 3 or 4 that i've used linux on did), which basically means that burning straight from hdd to the burner is just to i/o intensive for a reliable burn.  Glad you got it going.

---

### Post by fizgigg on 2005-10-29
I am having the same issue, and making an ISO image before hand did not help at all.  I checked all the normal stuff, and yes DMA is turned on for the drive.

After mounting the DVD I created manually, here is the output of dmesg | tail:

```
[4317736.588000] cdrom: This disc doesn't have any tracks I recognize!
[4317897.377000] ISO 9660 Extensions: Microsoft Joliet Level 1
[4317897.424000] ISOFS: changing to secondary root
[4350518.514000] cdrom: This disc doesn't have any tracks I recognize!
[4350912.555000] cdrom: This disc doesn't have any tracks I recognize!
[4351474.560000] cdrom: This disc doesn't have any tracks I recognize!
[4352159.690000] cdrom: This disc doesn't have any tracks I recognize!
[4352444.970000] attempt to access beyond end of device
[4352444.970000] hda: rw=0, want=68, limit=4
[4352444.970000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16

```

Below is the output of Gnomebaker log:

```
Executing 'builtin_dd if=/home/fizgigg/1_25.iso of=/dev/hda obs=32k seek=0'
/dev/hda: "Current Write Speed" is 8.2x1385KBps.
   1605632/4560959488 ( 0.0%) @0.0x, remaining 283:57
:-? the LUN appears to be stuck writing LBA=310h, retry in 70ms
   1605632/4560959488 ( 0.0%) @0.0x, remaining 473:16
   1605632/4560959488 ( 0.0%) @0.0x, remaining 615:14
:-? the LUN appears to be stuck writing LBA=310h, retry in 70ms
   1605632/4560959488 ( 0.0%) @0.0x, remaining 757:13
  11370496/4560959488 ( 0.2%) @2.1x, remaining 133:22
  34799616/4560959488 ( 0.8%) @5.0x, remaining 49:51
  62554112/4560959488 ( 1.4%) @5.9x, remaining 31:09
  90537984/4560959488 ( 2.0%) @5.9x, remaining 24:41
 118030336/4560959488 ( 2.6%) @5.8x, remaining 20:42
 145686528/4560959488 ( 3.2%) @5.8x, remaining 18:11
 173768704/4560959488 ( 3.8%) @5.9x, remaining 16:49
 201555968/4560959488 ( 4.4%) @5.9x, remaining 15:30
 229048320/4560959488 ( 5.0%) @5.8x, remaining 14:29
 256737280/4560959488 ( 5.6%) @5.9x, remaining 13:58
 285016064/4560959488 ( 6.2%) @6.0x, remaining 13:15
 312541184/4560959488 ( 6.9%) @5.8x, remaining 12:41
 340525056/4560959488 ( 7.5%) @5.9x, remaining 12:23
 368050176/4560959488 ( 8.1%) @5.8x, remaining 11:57
 395837440/4560959488 ( 8.7%) @5.9x, remaining 11:34
 404258816/4560959488 ( 8.9%) @1.8x, remaining 11:59
 404258816/4560959488 ( 8.9%) @0.0x, remaining 12:30
:-? the LUN appears to be stuck writing LBA=30310h, retry in 70ms
 404258816/4560959488 ( 8.9%) @0.0x, remaining 13:01
 421756928/4560959488 ( 9.2%) @3.7x, remaining 13:05
 453017600/4560959488 ( 9.9%) @6.6x, remaining 12:32
 489947136/4560959488 (10.7%) @7.8x, remaining 11:54
 526942208/4560959488 (11.6%) @7.8x, remaining 11:28
 564592640/4560959488 (12.4%) @8.0x, remaining 10:58
 601391104/4560959488 (13.2%) @7.8x, remaining 10:32
 638484480/4560959488 (14.0%) @7.8x, remaining 10:14
 675086336/4560959488 (14.8%) @7.7x, remaining 9:52
 712507392/4560959488 (15.6%) @7.9x, remaining 9:32
 748421120/4560959488 (16.4%) @7.6x, remaining 9:20
 784826368/4560959488 (17.2%) @7.7x, remaining 9:03
 821657600/4560959488 (18.0%) @7.8x, remaining 8:47
 855670784/4560959488 (18.8%) @7.2x, remaining 8:39
 893091840/4560959488 (19.6%) @7.9x, remaining 8:25
 929529856/4560959488 (20.4%) @7.7x, remaining 8:12
 966524928/4560959488 (21.2%) @7.8x, remaining 8:03
1003945984/4560959488 (22.0%) @7.9x, remaining 7:51
1040908288/4560959488 (22.8%) @7.8x, remaining 7:39
1078034432/4560959488 (23.6%) @7.9x, remaining 7:32
1115226112/4560959488 (24.5%) @7.9x, remaining 7:21
1151795200/4560959488 (25.3%) @7.7x, remaining 7:12
1188888576/4560959488 (26.1%) @7.8x, remaining 7:05
1225981952/4560959488 (26.9%) @7.8x, remaining 6:56
1259765760/4560959488 (27.6%) @7.1x, remaining 6:48
1297252352/4560959488 (28.4%) @7.9x, remaining 6:42
1334018048/4560959488 (29.2%) @7.8x, remaining 6:34
1371275264/4560959488 (30.1%) @7.9x, remaining 6:26
1407451136/4560959488 (30.9%) @7.7x, remaining 6:20
1437925376/4560959488 (31.5%) @6.4x, remaining 6:15
1474658304/4560959488 (32.3%) @7.8x, remaining 6:08
1511981056/4560959488 (33.2%) @7.9x, remaining 6:02
1549008896/4560959488 (34.0%) @7.8x, remaining 5:55
1585643520/4560959488 (34.8%) @7.7x, remaining 5:49
1622704128/4560959488 (35.6%) @7.8x, remaining 5:44
1657176064/4560959488 (36.3%) @7.3x, remaining 5:38
1694236672/4560959488 (37.1%) @7.8x, remaining 5:31
1731395584/4560959488 (38.0%) @7.9x, remaining 5:26
1767735296/4560959488 (38.8%) @7.7x, remaining 5:20
1805189120/4560959488 (39.6%) @7.9x, remaining 5:14
1841889280/4560959488 (40.4%) @7.8x, remaining 5:10
1879113728/4560959488 (41.2%) @7.9x, remaining 5:03
1916272640/4560959488 (42.0%) @7.9x, remaining 4:58
1953005568/4560959488 (42.8%) @7.8x, remaining 4:53
1990098944/4560959488 (43.6%) @7.8x, remaining 4:48
2027290624/4560959488 (44.4%) @7.9x, remaining 4:42
2060058624/4560959488 (45.2%) @6.9x, remaining 4:39
2096726016/4560959488 (46.0%) @7.8x, remaining 4:33
2133688320/4560959488 (46.8%) @7.8x, remaining 4:28
2170454016/4560959488 (47.6%) @7.8x, remaining 4:24
2207580160/4560959488 (48.4%) @7.9x, remaining 4:19
2244476928/4560959488 (49.2%) @7.8x, remaining 4:13
2281439232/4560959488 (50.0%) @7.8x, remaining 4:09
2318761984/4560959488 (50.8%) @7.9x, remaining 4:04
2355560448/4560959488 (51.6%) @7.8x, remaining 3:59
2392883200/4560959488 (52.5%) @7.9x, remaining 3:55
2429517824/4560959488 (53.3%) @7.7x, remaining 3:50
2460680192/4560959488 (54.0%) @6.6x, remaining 3:47
2497314816/4560959488 (54.8%) @7.7x, remaining 3:43
2534277120/4560959488 (55.6%) @7.8x, remaining 3:38
2571894784/4560959488 (56.4%) @8.0x, remaining 3:33
2605973504/4560959488 (57.1%) @7.2x, remaining 3:30
2642870272/4560959488 (57.9%) @7.8x, remaining 3:25
2679603200/4560959488 (58.8%) @7.8x, remaining 3:20
2713616384/4560959488 (59.5%) @7.2x, remaining 3:17
2750971904/4560959488 (60.3%) @7.9x, remaining 3:12
2787377152/4560959488 (61.1%) @7.7x, remaining 3:08
2824503296/4560959488 (61.9%) @7.9x, remaining 3:04
2858778624/4560959488 (62.7%) @7.2x, remaining 3:00
2895839232/4560959488 (63.5%) @7.8x, remaining 2:55
2932703232/4560959488 (64.3%) @7.8x, remaining 2:52
2969862144/4560959488 (65.1%) @7.9x, remaining 2:47
3004039168/4560959488 (65.9%) @7.2x, remaining 2:43
3040739328/4560959488 (66.7%) @7.8x, remaining 2:39
3077963776/4560959488 (67.5%) @7.9x, remaining 2:35
3112206336/4560959488 (68.2%) @7.2x, remaining 2:31
3148873728/4560959488 (69.0%) @7.8x, remaining 2:27
3185606656/4560959488 (69.8%) @7.8x, remaining 2:23
3223093248/4560959488 (70.7%) @7.9x, remaining 2:19
3256451072/4560959488 (71.4%) @7.1x, remaining 2:16
3293544448/4560959488 (72.2%) @7.8x, remaining 2:11
3330998272/4560959488 (73.0%) @7.9x, remaining 2:07
3367829504/4560959488 (73.8%) @7.8x, remaining 2:03
3401809920/4560959488 (74.6%) @7.2x, remaining 2:00
3438870528/4560959488 (75.4%) @7.8x, remaining 1:56
3475472384/4560959488 (76.2%) @7.7x, remaining 1:52
3512795136/4560959488 (77.0%) @7.9x, remaining 1:48
3547201536/4560959488 (77.8%) @7.3x, remaining 1:44
3583901696/4560959488 (78.6%) @7.8x, remaining 1:40
3620601856/4560959488 (79.4%) @7.8x, remaining 1:36
3654811648/4560959488 (80.1%) @7.2x, remaining 1:33
3692494848/4560959488 (81.0%) @8.0x, remaining 1:29
3728932864/4560959488 (81.8%) @7.7x, remaining 1:25
3766255616/4560959488 (82.6%) @7.9x, remaining 1:21
3800104960/4560959488 (83.3%) @7.2x, remaining 1:18
3837231104/4560959488 (84.1%) @7.9x, remaining 1:14
3874455552/4560959488 (84.9%) @7.9x, remaining 1:10
3911122944/4560959488 (85.8%) @7.8x, remaining 1:06
3945103360/4560959488 (86.5%) @7.2x, remaining 1:02
3982589952/4560959488 (87.3%) @7.9x, remaining 0:58
4017881088/4560959488 (88.1%) @7.5x, remaining 0:55
4051730432/4560959488 (88.8%) @7.2x, remaining 0:51
4084465664/4560959488 (89.6%) @6.9x, remaining 0:48
4121460736/4560959488 (90.4%) @7.8x, remaining 0:44
4155375616/4560959488 (91.1%) @7.2x, remaining 0:41
4190142464/4560959488 (91.9%) @7.4x, remaining 0:37
4226482176/4560959488 (92.7%) @7.7x, remaining 0:34
4260495360/4560959488 (93.4%) @7.2x, remaining 0:30
4297326592/4560959488 (94.2%) @7.8x, remaining 0:26
4331732992/4560959488 (95.0%) @7.3x, remaining 0:23
4368596992/4560959488 (95.8%) @7.8x, remaining 0:19
4402315264/4560959488 (96.5%) @7.1x, remaining 0:16
4439900160/4560959488 (97.3%) @7.9x, remaining 0:12
4473880576/4560959488 (98.1%) @7.2x, remaining 0:08
4510220288/4560959488 (98.9%) @7.7x, remaining 0:05
4544757760/4560959488 (99.6%) @7.3x, remaining 0:01
/dev/hda: flushing cache
/dev/hda: closing track
/dev/hda: closing disc
:-[ CLOSE SESSION failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
```

I am wondering if it failing to close the session is the problem, any ideas?

Thanks,
Cord

---

### Post by Bender NZ on 2005-10-29
Did you try writing at a lower speed? You're writing at 7-8x there which is quite fast - perhaps try manually setting it to 3-4x and see if it helps?

---

### Post by Bender NZ on 2005-10-30
Just thought I'd add - the burning was still touch and go, sometimes the disc was successful, sometimes it'd crap out. None of the times the buffer underrun protection would work though.

I managed to get around this by installing NeroLINUX and it works brilliantly, and burnfree works properly, plus the discs burn at full speed. Made a short thread with where to get it/how to install etc here: [http://www.ubuntuforums.org/showthread.php?t=84011](http://www.ubuntuforums.org/showthread.php?t=84011)

---

### Post by jeffreyvergara.NET on 2005-10-30
whats with the DMA on thing? I think I read something that DMA on is for old Hardwares (made 3yrs up) Im using k3b to burn data data DVD straight from my HD and don't have problem. And I dont remember turning DMA on.

---

### Post by fizgigg on 2005-10-30
Installing NeroLinux worked for me.  It looks like it is time to through some support to the maintainers of growisofs.

Thanks for the tip.

---

### Post by dickmorrell on 2005-10-30
There is an easier way

[http://ubuntuforums.org/showthread.php?t=84195]("http://ubuntuforums.org/showthread.php?t=84195")

---

