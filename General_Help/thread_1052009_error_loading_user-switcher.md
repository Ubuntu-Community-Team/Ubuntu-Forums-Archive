---
title: "error loading user-switcher"
date: 2009-01-27
forum: General Help
---

### Post by brainskins on 2009-01-27
I'm having a little issue with user-switcher. I'm running 8.10 and I have it set to boot into text mode. When I try to run startx it begins to load my desktop but then errors out. It tells me that there is a problem loading the user-switcher. Is there a way to just disable the user switcher ? This is a  server so I don't need the GUI that often but this is a problem.

---

### Post by brainskins on 2009-01-27
I reinstalled ubuntu desktop - that didn't work.

---

### Post by brainskins on 2009-01-27
Found a bug report - trying to reconfigure gdm now 

[https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/290509](https://bugs.launchpad.net/ubuntu/+source/fast-user-switch-applet/+bug/290509)

---

### Post by brainskins on 2009-01-27
so i ran dpkg-reconfigure gdm - and now it freezes when trying to boot

---

### Post by brainskins on 2009-01-27
Ok - so after doing a disk check it boots up again - now when i start x it loads up but its all pixelated and looks the pattern of an old ladys 1971 couch. Heres the output : 
X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux UBUNTU 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 27 11:51:15 2009
(==) Using config file: "/etc/X11/xorg.conf"
Error in I830WaitLpRing(), timeout for 2 seconds
pgetbl_ctl: 0x1ffe0001 getbl_err: 0x00000012
ipeir: 0x00000000 iphdr: 0x54f00006
LP ring tail: 0x00006aa0 head: 0x00006ac4 len: 0x0001f001 start 0x00000000
eir: 0x0000 esr: 0x0010 emr: 0xff7b
instdone: 0xff41 instpm: 0x0000
memmode: 0x00000000 instps: 0x00000031
hwstam: 0xfffe ier: 0x0002 imr: 0x053c iir: 0x0080
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring at virtual 0xaf910000 head 0x6ac4 tail 0x6aa0 count 32759
Ring end
space: 28 wanted 32

Fatal server error:
lockup


Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb80b3400]
2: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b20b80]
3: /usr/bin/X11/X [0x80d6b0a]
4: /usr/lib/xorg/modules/extensions//libglx.so [0xb7bdfbe9]
5: /usr/bin/X11/X(AbortDDX+0x79) [0x80a8b09]
6: /usr/bin/X11/X(AbortServer+0x28) [0x813c498]
7: /usr/bin/X11/X(FatalError+0x63) [0x813caa3]
8: /usr/lib/xorg/modules/drivers//intel_drv.so(I830WaitLpRing+0x201) [0xb7b15201]
9: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b3dc58]
10: /usr/lib/xorg/modules//libexa.so(exaFillRegionTiled+0x36f) [0xb7a2b17f]
11: /usr/lib/xorg/modules//libexa.so [0xb7a2b6a8]
12: /usr/bin/X11/X [0x8177a94]
13: /usr/bin/X11/X(miPaintWindow+0x231) [0x8110991]
14: /usr/bin/X11/X(miWindowExposures+0x142) [0x8110d02]
15: /usr/lib/xorg/modules/extensions//libdri.so(DRIWindowExposures+0x97) [0xb7b8ee17]
16: /usr/bin/X11/X [0x80d84ff]
17: /usr/bin/X11/X(MapWindow+0x303) [0x8077513]
18: /usr/bin/X11/X(InitRootWindow+0x100) [0x8077760]
19: /usr/bin/X11/X(main+0x416) [0x8071cb6]
20: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7cb7685]
21: /usr/bin/X11/X [0x8071101]
Saw signal 11.  Server aborting.
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

---

### Post by brainskins on 2009-01-27
Rebooted again - back to the user-switcher error

---

