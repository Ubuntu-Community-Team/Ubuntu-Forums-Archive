---
title: "Xorg crash"
date: 2013-04-02
forum: Desktop Environments
---

### Post by tyraen on 2013-04-02
Kernel: 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
xorg-server 2:1.13.0-0ubuntu6.1

This is the fourth or fifth time since setting up the machine I have encountered this freeze. When it happens, my display is unresponsive. It seems that applications continue to run in the backend, and possible that I could SSH in (did not have sshd running). I am not sure if I could have killed X. I am unable to switch to any TTY with CTRL-ALT-FKEY; even though the display doesn't update I've tried to blindly login and restart the box but it does not appear to be responding.

Here is the stacktrace from the most recent; I will start tracking these, but I am pretty sure that it is the same as the last one:

[ 36877.815] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f74824a9b76]
[ 36877.816] (EE) 1: /usr/bin/X (0x7f7482301000+0x1ac9a9) [0x7f74824ad9a9]
[ 36877.816] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f7481627000+0xfcb0) [0x7f7481636cb0]
[ 36877.817] (EE) 3: /lib/x86_64-linux-gnu/libc.so.6 (0x7f748028b000+0x802ef) [0x7f748030b2ef]
[ 36877.817] (EE) 4: /lib/x86_64-linux-gnu/libc.so.6 (__libc_malloc+0x75) [0x7f748030dfb5]
[ 36877.817] (EE) 5: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7f7481195000+0x45e3b) [0x7f74811dae3b]
[ 36877.817] (EE) 6: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7f7481195000+0x46e54) [0x7f74811dbe54]
[ 36877.817] (EE) 7: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (pixman_region_subtract+0x9c) [0x7f74811dd5dc]
[ 36877.817] (EE) 8: /usr/lib/xorg/modules/libexa.so (0x7f747e2a8000+0x5af6) [0x7f747e2adaf6]
[ 36877.817] (EE) 9: /usr/lib/xorg/modules/libexa.so (0x7f747e2a8000+0x83e0) [0x7f747e2b03e0]
[ 36877.817] (EE) 10: /usr/lib/xorg/modules/libexa.so (0x7f747e2a8000+0x4d3f) [0x7f747e2acd3f]
[ 36877.817] (EE) 11: /usr/bin/X (0x7f7482301000+0x130550) [0x7f7482431550]
[ 36877.817] (EE) 12: /usr/bin/X (ValidateGC+0x24) [0x7f7482369324]
[ 36877.817] (EE) 13: /usr/bin/X (0x7f7482301000+0x12371c) [0x7f748242471c]
[ 36877.817] (EE) 14: /usr/bin/X (miCompositeRects+0x8a) [0x7f74824248ca]
[ 36877.818] (EE) 15: /usr/bin/X (0x7f7482301000+0x12b615) [0x7f748242c615]
[ 36877.818] (EE) 16: /usr/bin/X (0x7f7482301000+0x55a91) [0x7f7482356a91]
[ 36877.818] (EE) 17: /usr/bin/X (0x7f7482301000+0x4456a) [0x7f748234556a]
[ 36877.818] (EE) 18: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7f74802ac76d]
[ 36877.818] (EE) 19: /usr/bin/X (0x7f7482301000+0x448ad) [0x7f74823458ad]

---

### Post by tyraen on 2013-04-02
Just got another one. I wondered if it was related to Suspending, but apparently not since I had only had the machine on for less than an hour. The stack trace is the same. I am on a Lenovo Thinkpad T510 with an Nvidia card using the Nouveau driver. Could be wrong, but there's nothing that looks directly Nouveau-related in the stack trace.

I've disabled Compositing in KWin now, since that also seems to be related (it has occurred a couple times while switching tasks).

---

### Post by oneone on 2013-12-03
Hi there,

I've got a Lenovo T510, model 43494JG with nvidia NVS3100M graphics ([http://goo.gl/eXXpSk](http://goo.gl/eXXpSk)). There problem here is the same, occasional crashes of the X server, that seem to be related to the use of 3D hardware acceleration. The problem occurs on Ubuntu 12.04, 13.04, 13.11 amd64 with nouveau driver. Using Gnome/Unity the crashes happen quite often (compiz uses 3D accel), running XFCE (Xubuntu) they are less frequent but do happen too and make the system effectively unusable. The crashes also happen when resuming from standby or switching from LCD to an external monitor. 

The model is listed as certified ([http://www.ubuntu.com/certification/hardware/201101-7181/](http://www.ubuntu.com/certification/hardware/201101-7181/)) for 12.04 32-bit. (Why 32-bit on this machine?) I actually would expect it to be working with 13.10 amd64, too. So what is the problem here?

I am not sure if my graphics card is broken or if it is a problem Ubuntu/X/nouveau. Running Win7 amd64 on the same machine works well (no crashes over days), so I assume the graphics card is OK.

Sometimes it is possible to switch to a text terminal or log in via ssh and restart lightdm (restart X). 

I tried to use the nvidia proprietary driver. I does not work at all. I wonder why because the specs say, that this card is supported? ([http://www.nvidia.com/Download/driverResults.aspx/69366/en-us](http://www.nvidia.com/Download/driverResults.aspx/69366/en-us))

Can anyone confirm this? I would like to be sure, it's not a hardware problem.

Are there any test utilities for nvidia cards to perform a hardware test of the graphics card.

---

