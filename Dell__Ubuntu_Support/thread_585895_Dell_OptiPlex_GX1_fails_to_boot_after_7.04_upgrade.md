---
title: "Dell OptiPlex GX1 fails to boot after 7.04 upgrade to 7.10"
date: 2007-10-21
forum: Dell  Ubuntu Support
---

### Post by jfehribach on 2007-10-21
This system ran adequately for several months with Ubuntu 7.04.  I upgraded to 7.10 and now it will not boot.  Details below.  I used this system mostly as a server for music files, and all data is safe, so I'm not too stressed.  Suggestions appreciated.  Thanks.

Jerry Fehribach

-----

Dell OptiPlex GX1 350Mhz
BIOS reports System Memory: 224 MB SDRAM
Video Memory: 8MB SGRAM
40 GB hard drive

GRUB shows 5 options:

1.  Ubuntu 7.10, kernel 2.6.22-14-generic [default]
    results in boot hang in about 30 seconds with about 10% of status bar filled in with orange 

2.  Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
    results in hangup after about a minute.  The last 5 lines shown on screen are:
	[  285.508785] input: PC Speaker as /class/input/input3
	[  286.163597] pnp: Device 01:01.01 activated.
	[  286.163597] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x3a0, speed 685kHz
	[  287.612374] rt18180: Bringing up iface
	[  287.821098]  rt18180: Card successfully reset

3.  Ubuntu 7.10, kernel 2.6.22-16-generic [default]
    results in boot hang in about 30 seconds with about 10% of status bar filled in with orange

4.  Ubuntu 7.10, kernel 2.6.22-16-generic (recovery mode)
    results in hangup after about a minute.  The last 5 lines shown on screen are:
	[  90.115058] input: PC Speaker as /class/input/input3
	[  90.367773] pnp: Device 01:01.01 activated.
	[  90.385006] gameport: NS558 PnP Gameport is pnp01:01.01/gameport0, io 0x3a0, speed 685kHz
	[  92.296487] rt18180: Bringing up iface
	[  92.505213] rt18180: Card successfully reset

5.  Ubuntu 7.10, memtest86+
    results in 0 errors reported after 2+ minutes WallTime

---

### Post by www.rzr.online.fr on 2007-10-28
Hi,

Sorry to be outopic bit I have a GX1 model too

And I have an issue with the video output like this guy :

[http://www.eio.com/public/motherbd.2004/0602.html](http://www.eio.com/public/motherbd.2004/0602.html)

Can you help ?
Thx

--
[http://rzr.online.fr/q/dell](http://rzr.online.fr/q/dell)

---

### Post by jfehribach on 2007-11-13
I decided to retire the old GX1 and use the 40GB disk for something else.

I have a Dell Dimension V400 that upgraded 7.04 to 7.10 with no problem, but this disaster in upgrading the GX1 is going to make me very nervous with every future upgrade.

Jerry Fehribach

---

