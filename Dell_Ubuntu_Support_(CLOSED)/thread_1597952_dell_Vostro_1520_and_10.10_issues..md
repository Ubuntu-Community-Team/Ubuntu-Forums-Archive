---
title: "dell Vostro 1520 and 10.10 issues."
date: 2010-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by israel.figueroa on 2010-10-15
Well, I updated from 10.04, fresh install (only /home preserved) 10.04 flawless, now in 10.10 have some issues.

First of all, everything work. But:

@work, I use ethernet cable and usb mouse and have NO issues there
@home, I use wifi and mousepad. I noticed some freezes (mouse pointer won't respond) so I did a top:

```

top - 23:27:35 up  1:28,  3 users,  load average: 3.36, 2.58, 2.06
Tasks: 180 total,   1 running, 179 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.9%us,  4.0%sy,  0.8%ni, 93.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3051792k total,  1222252k used,  1829540k free,    67072k buffers
Swap:   499708k total,        0k used,   499708k free,   462512k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 1147 root      20   0  184m  33m  14m S    3  1.1   2:46.81 Xorg                                                                                            
 2597 ifiguero  20   0  313m  16m  11m S    2  0.6   0:01.75 gnome-terminal                                                                                  
 2407 ifiguero  20   0  154m  55m  14m S    1  1.9   7:16.59 npviewer.bin                                                                                    
 2675 ifiguero  25   5  859m  73m  20m S    1  2.5   0:12.54 chromium-browse                                                                                 
 2233 ifiguero  25   5  859m  76m  20m S    1  2.6   0:31.17 chromium-browse                                                                                 
 1504 ifiguero  20   0  380m  46m  10m S    0  1.5   0:30.62 compiz                                                                                          
 1684 ifiguero  20   0 29180 1068  848 S    0  0.0   0:02.00 syndaemon                                                                                       
 2785 ifiguero  20   0 19276 1376  960 R    0  0.0   0:00.07 top                          
``` 

3.36 load average just with for browsing w chromium and pidgin. As you see, the programs aren't the blame.

so I did my work and checked the logs and the dmesg gives a lot of:

```
[ 4964.557857] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 4970.803857] psmouse.c: resync failed, issuing reconnect request
[ 5205.167059] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 5209.879311] psmouse.c: resync failed, issuing reconnect request
[ 5331.566584] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 5337.034374] psmouse.c: resync failed, issuing reconnect request

```

posted a few, but they are a lot. the mouse freezes, alt+tab and respond again.

In a unrelated issue, when log in, the wifi autoconnect but don't resolve dns. I have to manualy disable the network and re-enable it (in the wifi icon) and then when reconect works as expected.

some other specs:
```
ifiguero@ubuntu-vostro:~$ uname -a
Linux ubuntu-vostro 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:26:05 UTC 2010 x86_64 GNU/Linux

```

```
ifiguero@ubuntu-vostro:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0e:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)
1a:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01)

```

Regards,
Israel

---

### Post by azertyh on 2010-10-23
> **israel.figueroa said:**
> Well, I updated from 10.04, fresh install (only /home preserved) 10.04 flawless, now in 10.10 have some issues.

First of all, everything work. But:

@work, I use ethernet cable and usb mouse and have NO issues there
@home, I use wifi and mousepad. I noticed some freezes (mouse pointer won't respond) so I did a top:

```

top - 23:27:35 up  1:28,  3 users,  load average: 3.36, 2.58, 2.06
Tasks: 180 total,   1 running, 179 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.9%us,  4.0%sy,  0.8%ni, 93.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3051792k total,  1222252k used,  1829540k free,    67072k buffers
Swap:   499708k total,        0k used,   499708k free,   462512k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 1147 root      20   0  184m  33m  14m S    3  1.1   2:46.81 Xorg                                                                                            
 2597 ifiguero  20   0  313m  16m  11m S    2  0.6   0:01.75 gnome-terminal                                                                                  
 2407 ifiguero  20   0  154m  55m  14m S    1  1.9   7:16.59 npviewer.bin                                                                                    
 2675 ifiguero  25   5  859m  73m  20m S    1  2.5   0:12.54 chromium-browse                                                                                 
 2233 ifiguero  25   5  859m  76m  20m S    1  2.6   0:31.17 chromium-browse                                                                                 
 1504 ifiguero  20   0  380m  46m  10m S    0  1.5   0:30.62 compiz                                                                                          
 1684 ifiguero  20   0 29180 1068  848 S    0  0.0   0:02.00 syndaemon                                                                                       
 2785 ifiguero  20   0 19276 1376  960 R    0  0.0   0:00.07 top                          
```3.36 load average just with for browsing w chromium and pidgin. As you see, the programs aren't the blame.

so I did my work and checked the logs and the dmesg gives a lot of:

```
[ 4964.557857] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 4970.803857] psmouse.c: resync failed, issuing reconnect request
[ 5205.167059] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 5209.879311] psmouse.c: resync failed, issuing reconnect request
[ 5331.566584] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 5337.034374] psmouse.c: resync failed, issuing reconnect request

```posted a few, but they are a lot. the mouse freezes, alt+tab and respond again.



hello,
same issue, same messages in syslog.
for me, dell vostro 1015 and xubuntu 10.10.

---

