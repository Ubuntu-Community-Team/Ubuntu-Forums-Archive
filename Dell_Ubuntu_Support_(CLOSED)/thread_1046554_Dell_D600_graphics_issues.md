---
title: "Dell D600 graphics issues"
date: 2009-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Cannotcompute on 2009-01-21
I recently installed Ubuntu 8.10 on my Dell Latitude D600 laptop. I've been searching the forums for a solution, so I know that this is a "trouble laptop." I got the wireless working, it turned out I had a resource conflict. 

Everything was working fine until I installed ATI's proprietary video driver. Whenever I boot into Ubuntu now, it says that my video or display settings could not be detected.

I choose to re-detect them, but when I reboot I just get the same error again. I have already re-installed the ATI drivers 2 times. 

I read the logs to try to determine the error, but all I found was a very cryptic error. I'll upload the error logs in a few minutes.

Also, I think it worth mentioning that when I go to the Catalyst Control Center (part of the ATI driver) it says "There is no ATI driver installed, or it is not functioning properly." and the driver does not show up in the proprietary drivers list.

This error is the only thing keeping me from switching to Ubuntu full-time. thanks in advance for your help.

EDIT: Added the logs

The really cryptic part is at the end of Xorg.0.log, where it says
> (II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0                     <--------------
drmOpenDevice: open result is -1, (No such device or address)  <--------------
drmOpenDevice: open result is -1, (No such device or address)  <--------------
drmOpenDevice: Open failed                                     <--------------

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb7f12400]
2: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb7994c27]
3: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb796255a]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so [0xb79654fc]
5: /usr/X11R6/bin/X(InitOutput+0x96f) [0x80aac9f]
6: /usr/X11R6/bin/X(main+0x279) [0x8071b19]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b1a685]
8: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.

---

### Post by Cannotcompute on 2009-01-22
Nobody has a clue? :'(

---

### Post by pibb69173 on 2009-01-22
Gah i have the same-ish problem the video card is weird, check my thread man [http://ubuntuforums.org/showthread.php?t=1043902](http://ubuntuforums.org/showthread.php?t=1043902)        well when i tried installing the ATI dirvers

---

### Post by pibb69173 on 2009-01-22
wow ok my monitor works and all but when i go to change the resolution and what not it says uknown monitor.... why!!!, yea i need help with my video card

---

### Post by Cannotcompute on 2009-01-23
Yeah, my resolution change box also shows unknown monitor.

---

### Post by the.scarecrow on 2009-01-26
Hi Cannotcompute

I have a Dell D600 and the graphics card is working perfectly using both Intrepid and Hardy.

I did have problems with Hardy and followed these instructions to fix it.

[HTML]https://help.ubuntu.com/community/RadeonDriver
[/HTML]

I have the ATI Radeon 9000 and if you have the same you must not use drivers downloaded from ATI. You need to use the Open Source drivers and they work well enough for me to use Googleearth and Compiz, so there is light at the end of this tunnel.

I recently started using Intrepid and found that the graphics card worked straight from installation using the Open Source drivers.

---

### Post by MooseMagnet on 2009-01-28
I have Inspiron 1300. Feisty was great, but lots of problems with Intrepid, including weird graphics.

Firefox loads as black box, then scratchy distorted, and then various hard to describe distorted jumbled graphics.

Totem takes nearly 60 seconds to load, and during that time, it flicks and pops and has scratches and flashes.

With Firefox the screen randomly turns grey color as if it is going to sleep.

The touchpad clicks are enough to drive anyone mad. But I suspect it's something running in the background that's causing the machine to ignore the touchpad clicks, and not the touchpad itself.

How can a person get their laptop model included in the testing of next release?

---

### Post by egerzhoy on 2009-01-31
I have a dell Inspiron 600m (the same mobo as the D600), also running an ATI Radeon 9000 (that accursed thing!). I just installed 8.10 and have had huge problems trying to get the following to work:

1. 3D acceleration
2. tv-out

From my extensive searching on google and on these forums, it appears that ATI simply does not support its legacy cards after XORG 7.1

Since Ubuntu 8.10 uses XORG 7.4, there seems to be very little to be done to get 3D acceleration and tv-out to work.

If anyone has a workaround they are aware of, I would love to hear about it, because I installed Ubuntu especially to get Boxee to work with my TV.

---

### Post by arkashkin on 2009-02-02
> **egerzhoy said:**
> I have a dell Inspiron 600m (the same mobo as the D600), also running an ATI Radeon 9000 (that accursed thing!). I just installed 8.10 and have had huge problems trying to get the following to work:

1. 3D acceleration
2. tv-out

From my extensive searching on google and on these forums, it appears that ATI simply does not support its legacy cards after XORG 7.1

Since Ubuntu 8.10 uses XORG 7.4, there seems to be very little to be done to get 3D acceleration and tv-out to work.

If anyone has a workaround they are aware of, I would love to hear about it, because I installed Ubuntu especially to get Boxee to work with my TV.

Hi i have Dell D600, with Radeon 9000, i have managed to use tv- out,
go to - [http://wiki.archlinux.org/index.php/ATI](http://wiki.archlinux.org/index.php/ATI) , and read the tv-out section....

---

