---
title: "Unexpected session end with Steam (15.10)"
date: 2015-11-21
forum: Gaming &amp; Leisure
---

### Post by madtyn2 on 2015-11-21
Hello, 


since I last updated Ubuntu to 15.10 I'm having some problems while running some Steam games and trying to minimize windows or changing window with the game already started, becasue when I minimize, the session ends, and I have to introduce my login and pass again for opening session in Ubuntu and entering my desktop.


Two games with which I have noticed this are This War of Mine and Football Manager 2015, for example


I'm using 64bits architecture and I have already tried to change my graphical drivers three times through Ubuntu (nVidia graphical card) without success. I don't know if this may be a drivers problem, a Steam problem (although some other Steam games seem to work properly) or an Ubuntu problem (maybe it is a metaCity or compiz stuff???).


I have googled for this, but I couldn't found any solution or similar problem.


This is the dmesg | tail output for one of the crashes . 
Thanks in advanced.


[   36.324742] vboxdrv: Found 4 processor cores
[   36.343286] vboxdrv: TSC mode is Invariant, tentative frequency 3200021830 Hz
[   36.343288] vboxdrv: Successfully loaded version 5.0.4_Ubuntu (interface 0x00240000)
[   36.346537] VBoxNetFlt: Successfully started.
[   36.410463] VBoxNetAdp: Successfully started.
[   36.413310] VBoxPciLinuxInit
[   36.414871] vboxpci: IOMMU not found (not registered)
[  729.120876] show_signal_msg: 42 callbacks suppressed
[  729.120880] CIPCServer::Thr[4580]: segfault at 0 ip 00000000ee0a8294 sp 00000000ed1dbac0 error 4 in steamclient.so[ed5ae000+113a000]
[  733.732906] This War of Min[4899]: segfault at 0 ip 0000000008672e68 sp 00000000ff85f740 error 4 in This War of Mine[8048000+8df000]

---

