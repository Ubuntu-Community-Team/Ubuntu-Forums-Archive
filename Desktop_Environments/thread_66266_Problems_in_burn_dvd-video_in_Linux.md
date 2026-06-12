---
title: "Problems in burn dvd-video in Linux"
date: 2005-09-16
forum: Desktop Environments
---

### Post by vhalen on 2005-09-16
Hey guys, someone may help me?

I'm trying to migrate to Linux and I'm using Ubuntu 5.04. BUT I can't do it until I can burn my DVDs (videos) correctly and watch it...

The problem is :

- I burned a lot of movies in DVD in Windows. This DVDs works correctly in dvd players or in Windows or in Linux. I burned some DVDs in Linux and I can watch it in Windows ou DVD Players normally BUT this DVDs (burned in Linux using k3b or gnomebaker) didn't play in xine, mplayer or ogle. I don't know why this happen then I paste a lot of informations bellow :

==================================================================================== 
DVD burned in Linux: 
====================================================================================

The permissions in /dev/dvd are : 
$ ls -lai /dev/dvd 
2520 lrwxrwxrwx  1 root root 3 Set 12 05:24 /dev/dvd -> hdd

[fedora@localhost ~]$ ls -lai /media/cdrecorder/VIDEO_TS/ 
total 4571146 
1536 dr-xr-xr-x  2 fedora fedora       4096 Ago 24 22:18 . 
1472 dr-xr-xr-x  4 fedora fedora       2048 Ago 24 22:18 .. 
1542 -rw-rw-r--  1 fedora fedora       8192 Ago 24 20:56 VIDEO_TS.BUP 
1546 -rw-rw-r--  1 fedora fedora       8192 Ago 24 20:56 VIDEO_TS.IFO 
1550 -rw-rw-r--  1 fedora fedora      63488 Ago 24 20:47 VTS_01_0.BUP 
1554 -rw-rw-r--  1 fedora fedora      63488 Ago 24 20:47 VTS_01_0.IFO 
1558 -rw-rw-r--  1 fedora fedora 1073739776 Ago 24 20:37 VTS_01_1.VOB 
1563 -rw-rw-r--  1 fedora fedora 1073739776 Ago 24 20:41 VTS_01_2.VOB 
1567 -rw-rw-r--  1 fedora fedora 1073739776 Ago 24 20:44 VTS_01_3.VOB 
1571 -rw-rw-r--  1 fedora fedora  752865280 Ago 24 20:47 VTS_01_4.VOB 
1575 -rw-rw-r--  1 fedora fedora      24576 Ago 24 20:49 VTS_02_0.BUP 
1579 -rw-rw-r--  1 fedora fedora      24576 Ago 24 20:49 VTS_02_0.IFO 
1583 -rw-rw-r--  1 fedora fedora  498886656 Ago 24 20:49 VTS_02_1.VOB 
1587 -rw-rw-r--  1 fedora fedora      14336 Ago 24 20:51 VTS_03_0.BUP 
1591 -rw-rw-r--  1 fedora fedora      14336 Ago 24 20:51 VTS_03_0.IFO 
1600 -rw-rw-r--  1 fedora fedora   76107776 Ago 24 20:51 VTS_03_1.VOB 
1604 -rw-rw-r--  1 fedora fedora      18432 Ago 24 20:56 VTS_04_0.BUP 
1608 -rw-rw-r--  1 fedora fedora      18432 Ago 24 20:56 VTS_04_0.IFO 
1612 -rw-rw-r--  1 fedora fedora 131510272 Ago 24 20:56 VTS_04_1.VOB

The error message is :

[fedora@localhost ~]$ This is xine (X11 gui) - a free video player v0.99.4. 
(c) 2000-2004 The xine Team. 
libdvdread: Using libdvdcss version 1.2.9 for DVD access 
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed 
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed 
libdvdread: Can't open file VIDEO_TS.IFO. 
libdvdread: Using libdvdcss version 1.2.9 for DVD access 
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed 
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed 
libdvdread: Can't open file VIDEO_TS.IFO.

==================================================================================== 
Follow the same DVD burned in Windows : 
====================================================================================

[fedora@localhost ~]$ ls -lai /dev/dvd 
2520 lrwxrwxrwx  1 root root 3 Set 12 05:24 /dev/dvd -> hdd

[fedora@localhost ~]$ ls -lai /media/cdrecorder 
269 dr-xr-xr-x  4 4294967295 4294967295  136 Set  5 12:21 . 
4569601 drwxr-xr-x  5 root       root       4096 Set 12 08:25 .. 
272 dr-xr-xr-x  2 4294967295 4294967295   40 Set  5 12:20 AUDIO_TS 
271 dr-xr-xr-x  2 4294967295 4294967295 1340 Set  5 12:20 VIDEO_TS

[fedora@localhost ~]$ ls -lai /media/cdrecorder/VIDEO_TS/ 
271 dr-xr-xr-x  2 4294967295 4294967295       1340 Set  5 12:20 . 
269 dr-xr-xr-x  4 4294967295 4294967295        136 Set  5 12:21 .. 
276 -r-xr-xr-x  1 4294967295 4294967295      16384 Set  5 11:50 VIDEO_TS.BUP 
274 -r-xr-xr-x  1 4294967295 4294967295      16384 Set  5 11:50 VIDEO_TS.IFO 
275 -r-xr-xr-x  1 4294967295 4294967295     116736 Set  5 11:42 VIDEO_TS.VOB 
280 -r-xr-xr-x  1 4294967295 4294967295      36864 Set  5 11:43 VTS_01_0.BUP 
277 -r-xr-xr-x  1 4294967295 4294967295      36864 Set  5 11:43 VTS_01_0.IFO 
278 -r-xr-xr-x  1 4294967295 4294967295   77402112 Set  5 11:43 VTS_01_0.VOB 
279 -r-xr-xr-x  1 4294967295 4294967295   11208704 Set  5 11:43 VTS_01_1.VOB 
284 -r-xr-xr-x  1 4294967295 4294967295      18432 Set  5 11:43 VTS_02_0.BUP 
281 -r-xr-xr-x  1 4294967295 4294967295      18432 Set  5 11:43 VTS_02_0.IFO 
282 -r-xr-xr-x  1 4294967295 4294967295     116736 Set  5 11:43 VTS_02_0.VOB 
283 -r-xr-xr-x  1 4294967295 4294967295   76296192 Set  5 11:43 VTS_02_1.VOB 
290 -r-xr-xr-x  1 4294967295 4294967295      51200 Set  5 11:48 VTS_03_0.BUP 
285 -r-xr-xr-x  1 4294967295 4294967295      51200 Set  5 11:48 VTS_03_0.IFO 
286 -r-xr-xr-x  1 4294967295 4294967295     116736 Set  5 11:43 VTS_03_0.VOB 
287 -r-xr-xr-x  1 4294967295 4294967295 1073739776 Set  5 11:46 VTS_03_1.VOB 
288 -r-xr-xr-x  1 4294967295 4294967295 1073739776 Set  5 11:47 VTS_03_2.VOB 
289 -r-xr-xr-x  1 4294967295 4294967295  737466368 Set  5 11:48 VTS_03_3.VOB 
294 -r-xr-xr-x  1 4294967295 4294967295      32768 Set  5 11:50 VTS_04_0.BUP 
291 -r-xr-xr-x  1 4294967295 4294967295      32768 Set  5 11:50 VTS_04_0.IFO 
292 -r-xr-xr-x  1 4294967295 4294967295     116736 Set  5 11:48 VTS_04_0.VOB 
293 -r-xr-xr-x  1 4294967295 4294967295 1067003904 Set  5 11:50 VTS_04_1.VOB 
298 -r-xr-xr-x  1 4294967295 4294967295      18432 Set  5 11:50 VTS_05_0.BUP 
295 -r-xr-xr-x  1 4294967295 4294967295      18432 Set  5 11:50 VTS_05_0.IFO 
296 -r-xr-xr-x  1 4294967295 4294967295     116736 Set  5 11:50 VTS_05_0.VOB 
297 -r-xr-xr-x  1 4294967295 4294967295   81934336 Set  5 11:50 VTS_05_1.VOB 
====================================================================================

What happen to get this error only in DVD burned in Linux? This happen because permissions problems? How to burn DVD without permissions, like DVD burned in Windows? 

Thanks a lot... I'm newbie in Linux and I want to stay far from Windows :p

[]´s

---

### Post by jeffreyvergara.NET on 2005-09-16
hello, i used k3b before and it also didnt work well. I've seen Linux version of Nero Burning ROM, does anyone used this?

---

### Post by Hairy_Palms on 2005-09-16
try VLC it is available in synaptic it plays all DVDs i burn, if its a permission problem then try running k3b or gnome-baker as root with the command 
"sudo k3b" or "sudo gnomebaker"

---

### Post by vhalen on 2005-09-20
Hey Hairy_Palms,

I can see all my DVDs in normal players or in Windows. I'm thinking it's happen because remains something like DVD-Compat in programs... 

Did you already burn some movies in Linux? What program did you use to do this...?

thanks.

---

