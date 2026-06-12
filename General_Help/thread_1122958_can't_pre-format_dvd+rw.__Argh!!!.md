---
title: "can't pre-format dvd+rw.  Argh!!!"
date: 2009-04-11
forum: General Help
---

### Post by logos34 on 2009-04-11
New spindle of Maxell dvd+rw (4x speed).  (Discs are actually made by Ritek).

Tried K3b, Brasero, then the growisofs command in the terminal.  It seems to fail pre-formatting at ~85%.  K3b seems to be pre-formatting, then ejects the disc, then reloads, pre-formats a second time, and then spits out error message 'erasing failed'.  

Yet afterward the disc appears to be blank and unformatted (???).  Here's some more info:

> $ [B]growisofs -Z /dev/scd0 -R musicbackup23 musicbackup24
[/B]
Executing 'genisoimage -R musicbackup23 musicbackup24 | builtin_dd of=/dev/scd0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using PIERR000 for  /Pierre Boulez - Wiener Philharmoniker (Pierre Boulez - Berliner Philharmoniker)
Using PIERR001 for  /Pierre Boulez - Berliner Philharmoniker (Pierre Boulez - LSO)
Using _WIEN000.M3U;1 for  musicbackup24/Pierre Boulez - Wiener Philharmoniker/Bruckner_ Symphonie No. 8/CD/[Wiener Philharmoniker - Pierre Boulez] Bruckner, A ~ Symphony No.8 c-moll.m3u8 ([Wiener Philharmoniker - Pierre Boulez] Bruckner, A ~ Symphony No.8 c-moll.m3u)
  1.56% done, estimate finish Sat Apr 11 14:42:34 2009
  3.11% done, estimate finish Sat Apr 11 14:42:02 2009
  4.66% done, estimate finish Sat Apr 11 14:42:12 2009
[COLOR="Blue"]/dev/scd0: pre-formatting blank DVD+RW...
/dev/scd0: "Current Write Speed" is 2.5x1352KBps.[/COLOR]
[COLOR="Red"]:-[ WRITE@LBA=0h failed with SK=3h/ASC=57h/ACQ=00h]: Input/output error
:-( write failed: Input/output error[/COLOR]


------------------------------------------------------------------

$ dmesg | tail

[ 1329.810002]          res 40/00:00:00:4f:c2/00:00:00:00:00/00 Emask 0x4 (timeout)
[ 1329.810005] ata1.00: status: { DRDY }
[ 1330.166974] ata1: soft resetting link
[ 1330.330761] ata1.00: configured for UDMA/133
[ 1330.330788] ata1: EH complete
[ 1330.347005] sd 0:0:0:0: [sda] 240121728 512-byte hardware sectors (122942 MB)
[ 1330.362197] sd 0:0:0:0: [sda] Write Protect is off
[ 1330.362205] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1330.446987] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[COLOR="Red"][ 1374.390645] cdrom: This disc doesn't have any tracks I recognize![/COLOR]

--------------------------------------------------------------------

$ dvd+rw-format -force=full /dev/dvd

* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD+RW media detected.
- unimplemented command-line option for this media.
- you have the option to re-run dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

$ **dvd+rw-format -lead-out /dev/dvd**

* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* [COLOR="Blue"]4.7GB DVD+RW media detected.[/COLOR]
* [COLOR="Blue"]formatting 85.5[/COLOR][COLOR="Red"]|:-[ CLOSE SESSION failed with SK=5h/ASC=30h/ACQ=10h]: Wrong medium type[/COLOR]

----------------------------------------------------------------------

$ dvd+rw-mediainfo /dev/dvd

INQUIRY:                [ASUS    ][DRW-1608P2      ][1.41]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Ah, DVD+RW
 Media ID:              RITEK/004
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
 Write Speed #1:        2.4x1385=3324KB/s
 Speed Descriptor#0:    00/2295103 R@4.0x1385=5540KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#1:    00/2295103 R@2.4x1385=3324KB/s W@2.4x1385=3324KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ FORMAT CAPACITIES:
 unformatted:		2295104*2048=4700372992
 26h(0):		2295104*2048=4700372992
READ TRACK INFORMATION[#1]:
 Track State:           blank
 Track Start Address:   0*2KB
 Free Blocks:           2295104*2KB
 Track Size:            2295104*2KB
READ CAPACITY:          0*2048=0




dvd+rw-tools above shows '1' session, whereas k3b reports '0' seesions. (?)

[ATTACH]109509[/ATTACH]

This is the second dvd package I've tried--I can't believe ALL the discs are defective.  They are Ritek, which I thought were supposed to be pretty good, but then again I got them at Walmart, so no telling...

I'm able to burn and read the Memorex 4X dvd+rw (manufacturer: Infodisc) just fine...been using them for ages now, so it can't be the drive--besides I tried another drive (in windows and in linux), same prob.  It seems the problem is pre-formatting.  Only the first two out of the first spindle worked, the rest failed format, then I exchanged that pack for this one. 

WTF is the problem?

---

### Post by logos34 on 2009-04-11
I give up--time to try Memorex (InfoDisc) again.

guess the discs are all funked up...when they pre-format they do so at only 2.5x speed, rather than 4x.   Same actual speed in k3b (in the two or 3 instances I've managed to get that far!).  One of the successful writes failed verify.

it wouldn't surprise me if these were rejects Maxell decided to dump on Walmart

---

### Post by mc4man on 2009-04-11
Maybe they are 'bad' disks, I have a pack of the same, preformat fine with Imgburn (using the quick option - scratch that - there is no quick on the 'preformat'

Shows exact same info when blank
> 
doug@doug-desktop:~$ dvd+rw-mediainfo /dev/dvd
INQUIRY:                [ATAPI   ][DVD A  DH20A4P  ][9P59]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         1Ah, DVD+RW
 Media ID:              RITEK/004
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
 Write Speed #1:        2.4x1385=3324KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     4.0x1385=5540KB/s@[0 -> 0]
 Speed Descriptor#0:    00/0 R@4.8x1385=6648KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#1:    00/0 R@4.8x1385=6648KB/s W@2.4x1385=3324KB/s
READ DVD STRUCTURE[#0h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2295104*2KB=4700372992
READ DISC INFORMATION:
 Disc status:           blank
 Number of Sessions:    1
 State of Last Session: empty
 "Next" Track:          1
 Number of Tracks:      1
READ FORMAT CAPACITIES:
 unformatted:		2295104*2048=4700372992
 26h(0):		2295104*2048=4700372992
READ TRACK INFORMATION[#1]:
 Track State:           blank
 Track Start Address:   0*2KB
 Free Blocks:           2295104*2KB
 Track Size:            2295104*2KB
READ CAPACITY:          0*2048=0



---

### Post by logos34 on 2009-04-12
ok, I'll try ONE more time with ImgBurn, but I already tried InfraRecorder on windows and no go...

---

### Post by logos34 on 2009-04-12
forget it---I just updated to latest Imgburn 2.4.40 vers. and now it doesn't even detect my cd/dvd drive (!!)...wtf..I don't have time for this...if k3b can successfully  pre-format some (a couple at least) but not others, it must be faulty discs...I'll just excahnge them for memorex and hopefully have done with it

---

### Post by logos34 on 2009-04-14
dvd saga (continued):

Seems some cd/dvd players have trouble finalizing Ritek 004 discs, so maybe it's the make (and not faulty discs per se)...At any rate, the Memorex (Infodisc/A10) have worked pretty well for me, so if they're still the same I'll go with those...

Boy, this has been a lesson in the bewildering variety and quality of optical media.  It's hit-and-miss...there's no way to tell if discs will work properly on your drive until you actually try them (unless people at like cdfreaks.com have posted the info in the forums)

Newest version of Imageburn works now that I changed the drive type for cdrom in winecfg.  But it
s not the burn application that's causing the problem.

---

### Post by mc4man on 2009-04-14
> It's hit-and-miss...there's no way to tell if discs.....

That's one of the problems with most 'name' brand media (with notable exceptions of verbatium and taiyo yuden), you can never be 100% sure whose media they've used on the batch you buy.
I think in the past i've had memorex dvd-rw's by ridata, ritek, ect.

While i don't like memorex for dvdr or dvd-dl, their dvd-rw has been very reliable

For Imgburn I've switched the I/O from the default of SPTI to the first one listed - ASPI-WINASPI32.dll
(takes drive detection away from winecfg and directly to imgburn

---

### Post by SunnyRabbiera on 2009-04-14
Personally I buy Maxell often as they seem good in both areas (DVD and CD's)
But yes sounds like a bad batch though

---

### Post by logos34 on 2009-04-14
> **mc4man said:**
> That's one of the problems with most 'name' brand media (with notable exceptions of verbatium and taiyo yuden), you can never be 100% sure whose media they've used on the batch you buy.
I think in the past i've had memorex dvd-rw's by ridata, ritek, ect.

While i don't like memorex for dvdr or dvd-dl, their dvd-rw has been very reliable


yes, I generally hate memorex (that is, their choice of disc manufacturers)--EXCEPT, like you say, in dvd+rw. Oh, and their dvd+r (Ricoh) worked fine for me once upon a time (before my drive decided it would no longer reliably write dvd+r!) 

And yes, Verbatim seems pretty reliable, and I'm always looking for sales on that brand.

> **SunnyRabbiera said:**
> Personally I buy Maxell often as they seem good in both areas (DVD and CD's)
But yes sounds like a bad batch though

I swear by Maxell for CD (at least they used to be reliable.  Love my High-speed 10x cd-rw.  Make perfect audiocds too (as long as burned at 4x)

---

### Post by logos34 on 2009-04-14
ok, here's sth else I don't understand.

I just tried to rejuvenate an old Memorex dvd+rw (Infodisc/A10) that was proving hard to verify ("problem reading sectors..." message)...I nullified it but the operation seems to have failed:
> 
$ **growisofs -Z /dev/dvd=/dev/zero**

WARNING: /dev/dvd already carries isofs!
About to execute 'builtin_dd if=/dev/zero of=/dev/dvd obs=32k seek=0'
/dev/dvd: "Current Write Speed" is 4.1x1352KBps.
    1605632/4700372992 ( 0.0%) @0.0x, remaining 195:05 RBU 100.0% UBU   2.0%
    1605632/4700372992 ( 0.0%) @0.0x, remaining 341:25 RBU 100.0% UBU 100.0%
    1605632/4700372992 ( 0.0%) @0.0x, remaining 487:44 RBU 100.0% UBU 100.0%
    1605632/4700372992 ( 0.0%) @0.0x, remaining 682:50 RBU 100.0% UBU 100.0%
    1605632/4700372992 ( 0.0%) @0.0x, remaining 829:09 RBU 100.0% UBU 100.0%
   17858560/4700372992 ( 0.4%) @3.5x, remaining 87:24 RBU 100.0% UBU  57.1%
   36569088/4700372992 ( 0.8%) @4.1x, remaining 51:00 RBU 100.0% UBU  53.1%
   54558720/4700372992 ( 1.2%) @3.9x, remaining 38:19 RBU 100.0% UBU  59.2%
   73465856/4700372992 ( 1.6%) @4.1x, remaining 31:29 RBU 100.0% UBU  57.1%
   91553792/4700372992 ( 1.9%) @3.9x, remaining 28:31 RBU 100.0% UBU  55.1%
  110526464/4700372992 ( 2.4%) @4.1x, remaining 25:36 RBU 100.0% UBU  53.1%
  128679936/4700372992 ( 2.7%) @3.9x, remaining 23:41 RBU 100.0% UBU  55.1%
  
...

 4646633472/4700372992 (98.9%) @3.9x, remaining 0:09 RBU 100.0% UBU  53.1%
 4665442304/4700372992 (99.3%) @4.1x, remaining 0:06 RBU 100.0% UBU  57.1%
 4683399168/4700372992 (99.6%) @3.9x, remaining 0:03 RBU 100.0% UBU  55.1%
[COLOR="Red"]:-[ WRITE@LBA=230540h failed with SK=5h/ASC=21h/ACQ=02h]: Invalid argument
:-( write failed: Invalid argument[/COLOR]
/dev/dvd: flushing cache
/dev/dvd: stopping de-icing
/dev/dvd: writing lead-out
/dev/dvd: reloading tray


Now I'm fully aware you don't need to format dvd+rw's after the initial session, only overwrite them (excessive formatting renders them [unstable]("http://fy.chalmers.se/~appro/linux/DVD+RW/#plusvsminus")).  But I thought maybe it would clear the problem sectors (in the same way doing full format for cd-rw's).

But I just did a small test burn, it didn't warn me about overwrite, so I guess it was successfully blanked after all, despite the dvd+rw-tools message. Write successfull and verified.  Now let's burn the whole disc and see if it verifies...

---

### Post by logos34 on 2009-04-16
I got some slow Memorex (2x) dvd-rw, but exchanged them for some faster 4x OfficeDepot brand on sale (at least they're *supposed* to be faster).  I feared they were el cheapo crap, and it turns out I was right: upon inspection the discs ("Ativa") are made by CMC Magnetics, and the disc id CMCW03 turns up as "4th-class" (junk) on [this dvd media list]("http://www.hardwareforums.com/dvd-media-quality-guide-16348/")!!  I'm burning one right now and it only going at 2x!!!  

What do I have to do to get some decent DVD+/-RW without paying an arm and leg???

---

