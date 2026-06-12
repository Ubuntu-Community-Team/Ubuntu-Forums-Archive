---
title: "Burning problems, K3B"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Pitou on 2006-07-24
Hello,

I'm having a lot of problems burning DVD lately.

1 out of 2 DVD is a coaster.

Here is the lastlog I got from K3B:

[System] K3b Version: 0.12.14
[System] KDE Version: 3.5.3
[System] QT Version:  3.3.6
[System] Kernel:      2.6.15-26-686
[Devices] TOSHIBA DVD-ROM SD-M1612 J808 (/dev/hda, ) at /media/cdrom0 [CD-ROM; D
VD-ROM] [DVD-ROM; CD-ROM] [None]
[Devices] PIONEER DVD-RW  DVR-109 1.58 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-R
W; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM;
DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Res
tricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM;
 CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; R
estricted Overwrite; Layer Jump]
[Used versions] growisofs: 5.21
[growisofs command:] /usr/bin/X11/growisofs -Z /dev/hdc=/dev/fd/0 -use-the-force
-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:1078112 -dvd-
compat -speed=1
[growisofs] Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdc obs=32k seek=0'
[growisofs] /dev/hdc: "Current Write Speed" is 1.0x1385KBps.
[growisofs] :-? the LUN appears to be stuck writing LBA=800h, retry in 0ms
[growisofs] :-[ WRITE@LBA=80000800h failed with SK=2h/ASC=04h/ACQ=08h]: Resource
 temporarily unavailable
[growisofs] :-( write failed: Resource temporarily unavailable
[growisofs] /dev/hdc: flushing cache
[growisofs] /dev/hdc: updating RMA
[growisofs] /dev/hdc: closing disc


Thank you.

Pitou!

---

### Post by JoWilly on 2006-07-24
Have you tried nerolinux ? It uses the full nero 6.6.4 api and therefore bypasses the linux tools.

---

### Post by Pitou on 2006-07-24
No, but I just saw that growisofs 5.21 has problems with my Pioneer 109.

It seems to be fixed in version 6.0 and later.

Any idea how to install the latest growisofs in kubuntu dapper?

Thanks.

Pitou!

---

### Post by kinematic on 2006-07-24
or maybe the devs should update growisofs to the latest version.....i suspect that would also clear up a lot of problems.

---

### Post by Pitou on 2006-07-24
I just removed dvd+rw tools with adept and manually installed dvd+rw-tools_6.1-2_i386.deb from the debian site ([http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fd%2Fdvd%2Brw-tools%2Fdvd%2Brw-tools_6.1-2_i386.deb&md5sum=f3de999a0eb2077e52bc0bd06e9bd521&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fd%2Fdvd%2Brw-tools%2Fdvd%2Brw-tools_6.1-2_i386.deb&md5sum=f3de999a0eb2077e52bc0bd06e9bd521&arch=i386&type=main))

Everything is working fine now! Even my FIFO buffer is not acting like crazy.

Here is the complete log from my last burn:

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.3
QT Version:  3.3.6
Kernel:      2.6.15-26-686
Devices
-----------------------
TOSHIBA DVD-ROM SD-M1612 J808 (/dev/hda, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

PIONEER DVD-RW  DVR-109 1.58 (/dev/hdc, ) at /media/cdrom1 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-R Dual Layer Jump; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite; Layer Jump]
Used versions
-----------------------
growisofs: 6.1

growisofs
-----------------------
Executing 'builtin_dd if=image.iso of=/dev/hdc obs=32k seek=0'
/dev/hdc: "Current Write Speed" is 4.1x1385KBps.
  20938752/2207973376 ( 0.9%) @3.7x, remaining 8:42 RBU 100.0%
  39059456/2207973376 ( 1.8%) @3.8x, remaining 7:24 RBU 100.0%
  58064896/2207973376 ( 2.6%) @4.0x, remaining 7:24 RBU 99.4%
  76251136/2207973376 ( 3.5%) @3.8x, remaining 6:59 RBU 100.0%
  94666752/2207973376 ( 4.3%) @3.9x, remaining 6:41 RBU 99.9%
 113442816/2207973376 ( 5.1%) @3.9x, remaining 6:46 RBU 100.0%
 131629056/2207973376 ( 6.0%) @3.8x, remaining 6:34 RBU 100.0%
 150634496/2207973376 ( 6.8%) @4.0x, remaining 6:22 RBU 100.0%
 168755200/2207973376 ( 7.6%) @3.8x, remaining 6:26 RBU 100.0%
 187793408/2207973376 ( 8.5%) @4.0x, remaining 6:16 RBU 100.0%
 205946880/2207973376 ( 9.3%) @3.8x, remaining 6:09 RBU 100.0%
 224460800/2207973376 (10.2%) @3.9x, remaining 6:11 RBU 100.0%
 243138560/2207973376 (11.0%) @3.9x, remaining 6:03 RBU 100.0%
 261292032/2207973376 (11.8%) @3.8x, remaining 5:57 RBU 100.0%
 280330240/2207973376 (12.7%) @4.0x, remaining 5:57 RBU 100.0%
 298418176/2207973376 (13.5%) @3.8x, remaining 5:51 RBU 100.0%
 317489152/2207973376 (14.4%) @4.0x, remaining 5:45 RBU 100.0%
 335609856/2207973376 (15.2%) @3.8x, remaining 5:45 RBU 100.0%
 354222080/2207973376 (16.0%) @3.9x, remaining 5:40 RBU 100.0%
 372834304/2207973376 (16.9%) @3.9x, remaining 5:34 RBU 100.0%
 390955008/2207973376 (17.7%) @3.8x, remaining 5:34 RBU 100.0%
 408420352/2207973376 (18.5%) @3.7x, remaining 5:30 RBU 100.0%
 426278912/2207973376 (19.3%) @3.8x, remaining 5:26 RBU 100.0%
 445382656/2207973376 (20.2%) @4.0x, remaining 5:24 RBU 100.0%
 463503360/2207973376 (21.0%) @3.8x, remaining 5:19 RBU 100.0%
 481787904/2207973376 (21.8%) @3.9x, remaining 5:15 RBU 99.9%
 500695040/2207973376 (22.7%) @4.0x, remaining 5:13 RBU 100.0%
 518848512/2207973376 (23.5%) @3.8x, remaining 5:09 RBU 100.0%
 537985024/2207973376 (24.4%) @4.0x, remaining 5:07 RBU 100.0%
 556072960/2207973376 (25.2%) @3.8x, remaining 5:03 RBU 100.0%
 575045632/2207973376 (26.0%) @4.0x, remaining 4:58 RBU 99.4%
 593231872/2207973376 (26.9%) @3.8x, remaining 4:56 RBU 100.0%
 611483648/2207973376 (27.7%) @3.9x, remaining 4:52 RBU 100.0%
 630489088/2207973376 (28.6%) @4.0x, remaining 4:47 RBU 100.0%
 648609792/2207973376 (29.4%) @3.8x, remaining 4:46 RBU 100.0%
 667680768/2207973376 (30.2%) @4.0x, remaining 4:41 RBU 100.0%
 685867008/2207973376 (31.1%) @3.8x, remaining 4:37 RBU 100.0%
 704380928/2207973376 (31.9%) @3.9x, remaining 4:35 RBU 99.9%
 723058688/2207973376 (32.7%) @3.9x, remaining 4:31 RBU 100.0%
 741146624/2207973376 (33.6%) @3.8x, remaining 4:27 RBU 100.0%
 760250368/2207973376 (34.4%) @4.0x, remaining 4:24 RBU 100.0%
 778338304/2207973376 (35.3%) @3.8x, remaining 4:20 RBU 100.0%
 797409280/2207973376 (36.1%) @4.0x, remaining 4:16 RBU 100.0%
 813826048/2207973376 (36.9%) @3.5x, remaining 4:15 RBU 100.0%
 832208896/2207973376 (37.7%) @3.9x, remaining 4:11 RBU 99.5%
 850984960/2207973376 (38.5%) @4.0x, remaining 4:07 RBU 100.0%
 869203968/2207973376 (39.4%) @3.8x, remaining 4:04 RBU 100.0%
 888274944/2207973376 (40.2%) @4.0x, remaining 4:00 RBU 100.0%
 906395648/2207973376 (41.1%) @3.8x, remaining 3:56 RBU 100.0%
 924811264/2207973376 (41.9%) @3.9x, remaining 3:54 RBU 100.0%
 943652864/2207973376 (42.7%) @4.0x, remaining 3:50 RBU 100.0%
 961806336/2207973376 (43.6%) @3.8x, remaining 3:46 RBU 100.0%
 980877312/2207973376 (44.4%) @4.0x, remaining 3:43 RBU 100.0%
 999030784/2207973376 (45.2%) @3.8x, remaining 3:40 RBU 100.0%
1017708544/2207973376 (46.1%) @3.9x, remaining 3:36 RBU 100.0%
1036255232/2207973376 (46.9%) @3.9x, remaining 3:33 RBU 100.0%
1054375936/2207973376 (47.8%) @3.8x, remaining 3:30 RBU 100.0%
1073512448/2207973376 (48.6%) @4.0x, remaining 3:26 RBU 100.0%
1091665920/2207973376 (49.4%) @3.8x, remaining 3:23 RBU 100.0%
1110212608/2207973376 (50.3%) @3.9x, remaining 3:19 RBU 99.9%
1128857600/2207973376 (51.1%) @3.9x, remaining 3:15 RBU 100.0%
1147011072/2207973376 (51.9%) @3.8x, remaining 3:13 RBU 100.0%
1166082048/2207973376 (52.8%) @4.0x, remaining 3:09 RBU 100.0%
1184169984/2207973376 (53.6%) @3.8x, remaining 3:05 RBU 100.0%
1203240960/2207973376 (54.5%) @4.0x, remaining 3:02 RBU 100.0%
1219264512/2207973376 (55.2%) @3.4x, remaining 3:00 RBU 100.0%
1238368256/2207973376 (56.1%) @4.0x, remaining 2:56 RBU 100.0%
1256521728/2207973376 (56.9%) @3.8x, remaining 2:53 RBU 100.0%
1274904576/2207973376 (57.7%) @3.9x, remaining 2:49 RBU 100.0%
1293713408/2207973376 (58.6%) @4.0x, remaining 2:46 RBU 100.0%
1311866880/2207973376 (59.4%) @3.8x, remaining 2:43 RBU 100.0%
1330937856/2207973376 (60.3%) @4.0x, remaining 2:39 RBU 100.0%
1349124096/2207973376 (61.1%) @3.8x, remaining 2:35 RBU 100.0%
1367670784/2207973376 (61.9%) @3.9x, remaining 2:32 RBU 99.9%
1386348544/2207973376 (62.8%) @3.9x, remaining 2:29 RBU 100.0%
1404469248/2207973376 (63.6%) @3.8x, remaining 2:26 RBU 100.0%
1423540224/2207973376 (64.5%) @4.0x, remaining 2:22 RBU 100.0%
1441693696/2207973376 (65.3%) @3.8x, remaining 2:19 RBU 100.0%
1460142080/2207973376 (66.1%) @3.9x, remaining 2:16 RBU 100.0%
1479016448/2207973376 (67.0%) @4.0x, remaining 2:12 RBU 100.0%
1497169920/2207973376 (67.8%) @3.8x, remaining 2:09 RBU 100.0%
1516240896/2207973376 (68.7%) @4.0x, remaining 2:05 RBU 99.3%
1534590976/2207973376 (69.5%) @3.9x, remaining 2:02 RBU 100.0%
1552777216/2207973376 (70.3%) @3.8x, remaining 1:58 RBU 100.0%
1571913728/2207973376 (71.2%) @4.0x, remaining 1:55 RBU 99.2%
1590034432/2207973376 (72.0%) @3.8x, remaining 1:52 RBU 100.0%
1608286208/2207973376 (72.8%) @3.9x, remaining 1:48 RBU 100.0%
1624997888/2207973376 (73.6%) @3.5x, remaining 1:46 RBU 100.0%
1644068864/2207973376 (74.5%) @4.0x, remaining 1:42 RBU 100.0%
1662189568/2207973376 (75.3%) @3.8x, remaining 1:39 RBU 100.0%
1680900096/2207973376 (76.1%) @3.9x, remaining 1:35 RBU 99.9%
1699446784/2207973376 (77.0%) @3.9x, remaining 1:32 RBU 100.0%
1717567488/2207973376 (77.8%) @3.8x, remaining 1:29 RBU 100.0%
1736671232/2207973376 (78.7%) @4.0x, remaining 1:25 RBU 100.0%
1754890240/2207973376 (79.5%) @3.8x, remaining 1:22 RBU 100.0%
1773142016/2207973376 (80.3%) @3.9x, remaining 1:18 RBU 99.9%
1792147456/2207973376 (81.2%) @4.0x, remaining 1:15 RBU 100.0%
1810268160/2207973376 (82.0%) @3.8x, remaining 1:12 RBU 100.0%
1829339136/2207973376 (82.9%) @4.0x, remaining 1:08 RBU 100.0%
1847459840/2207973376 (83.7%) @3.8x, remaining 1:05 RBU 100.0%
1865711616/2207973376 (84.5%) @3.9x, remaining 1:02 RBU 100.0%
1884749824/2207973376 (85.4%) @4.0x, remaining 0:58 RBU 100.0%
1902903296/2207973376 (86.2%) @3.8x, remaining 0:55 RBU 100.0%
1921974272/2207973376 (87.0%) @4.0x, remaining 0:51 RBU 99.9%
1940094976/2207973376 (87.9%) @3.8x, remaining 0:48 RBU 100.0%
1958641664/2207973376 (88.7%) @3.9x, remaining 0:45 RBU 99.9%
1977417728/2207973376 (89.6%) @4.0x, remaining 0:41 RBU 100.0%
1995636736/2207973376 (90.4%) @3.8x, remaining 0:38 RBU 100.0%
2014609408/2207973376 (91.2%) @4.0x, remaining 0:35 RBU 99.4%
2031026176/2207973376 (92.0%) @3.5x, remaining 0:32 RBU 99.8%
2049474560/2207973376 (92.8%) @3.9x, remaining 0:28 RBU 100.0%
2067595264/2207973376 (93.6%) @3.8x, remaining 0:25 RBU 100.0%
2086764544/2207973376 (94.5%) @4.0x, remaining 0:22 RBU 100.0%
2104885248/2207973376 (95.3%) @3.8x, remaining 0:18 RBU 100.0%
2123137024/2207973376 (96.2%) @3.9x, remaining 0:15 RBU 100.0%
2142208000/2207973376 (97.0%) @4.0x, remaining 0:11 RBU 100.0%
2160361472/2207973376 (97.8%) @3.8x, remaining 0:08 RBU 100.0%
2178973696/2207973376 (98.7%) @3.9x, remaining 0:05 RBU 86.4%
2197651456/2207973376 (99.5%) @3.9x, remaining 0:01 RBU 30.8%
/dev/hdc: flushing cache
/dev/hdc: updating RMA
/dev/hdc: closing disc

growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdc=image.iso -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=4 -use-the-force-luke=bufsize:32m 



Pitou!

---

### Post by JoWilly on 2006-07-24
Don't forget to post a bug report with your solution in launchpad to inform the developers of the problem.

---

### Post by Pitou on 2006-07-24
sure, How do I do that?,

Also How do I change the thread to add solved in the header?

---

### Post by JoWilly on 2006-07-24
> **Pitou said:**
> sure, How do I do that?,

Also How do I change the thread to add solved in the header?

File a bug here  : [https://launchpad.net/distros/ubuntu/+filebug]("https://launchpad.net/distros/ubuntu/+filebug")

You can edit your post (and title) by clicking on the edit icon (go to your 1st post).

---

### Post by Pitou on 2006-07-24
my first post has the correct subject, but not the thread. I still don't see where to edit it.

---

### Post by RichJacot on 2006-08-06
Hello,  I was having this exact same issue.  I upgraded to rw-tools_6.1-2_i386.deb and so far I have not had an issue.  Thank you!

---

### Post by Pitou on 2006-08-07
Great!

Pitou!

---

