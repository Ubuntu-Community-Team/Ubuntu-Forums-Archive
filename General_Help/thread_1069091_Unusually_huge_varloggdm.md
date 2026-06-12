---
title: "Unusually huge /var/log/gdm"
date: 2009-02-13
forum: General Help
---

### Post by karmapia on 2009-02-13
I'm having this problem consistantly. The exact same problem occurs every day on the same time.
I'm having unusually huge GDM log files, which are so huge, and the system goes down everyday on the same time.
I've been deleting this files manually until now, but I'm growing tired of it and seeking for help to stop this. Thanks in advance :D

```

[COLOR="Red"]admin@ubuntu:/var/log/gdm$ ls -l[/COLOR]
&#54633;&#44228; 5525212
-rw-r--r-- 1 root root       1179 2009-02-13 14:32 :0.log
-rw-r--r-- 1 root root 1162641408 2009-02-13 14:30 :0.log.1
-rw-r--r-- 1 root root 1496395002 2009-02-13 14:06 :0.log.2
-rw-r--r-- 1 root root 1496835908 2009-02-13 13:36 :0.log.3
-rw-r--r-- 1 root root 1496395002 2009-02-13 13:07 :0.log.4

[COLOR="Red"]admin@ubuntu:/media/JPSystem$ more :0.log.1[/COLOR]
X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-11-generic #1 SMP Thu Jan 29 19:24
:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 13 14:06:31 2009
(==) Using config file: "/etc/X11/xorg.conf"
Error in I830WaitLpRing(), timeout for 2 seconds
pgetbl_ctl: 0x7ffc0001 getbl_err: 0x00000000
ipeir: 0x00000000 iphdr: 0x3e99999a
LP ring tail: 0x000001b0 head: 0x00000000 len: 0x0001f001 start 0x00000000
eir: 0x0000 esr: 0x0001 emr: 0xffff
instdone: 0xffc1 instpm: 0x0000
memmode: 0x00000108 instps: 0x800f0040
hwstam: 0xfffe ier: 0x0002 imr: 0x0000 iir: 0x00c0
Ring at virtual 0xa775f000 head 0x0 tail 0x1b0 count 108
Ring at virtual 0xa775f000 head 0x0 tail 0x1b0 count 108
	0001ff00: 7d800003	3D/Media Reserved (pipe 3 op 5 sub 128)
	0001ff04: 00000000
	0001ff08: 00000000
	0001ff0c: 035f047f
	0001ff10: 00000000
	0001ff14: 00000000	MI_NOOP                                  1
	0001ff18: 18800080	MI_BATCH_BUFFER_START                    2
	0001ff1c: 0718b001
Batch buffer at 0x0718b001 {
[COLOR="Red"](I'm assuming this would go infinitely.)[/COLOR]
	0718b001: 00000000	MI_NOOP                                  1
	0718b005: 00000000	MI_NOOP                                  1
	0718b009: 00000000	MI_NOOP                                  1
	0718b00d: 00000000	MI_NOOP                                  1
	0718b011: 00000000	MI_NOOP                                  1
	0718b015: 00000000	MI_NOOP                                  1
	0718b019: 00000000	MI_NOOP                                  1
	0718b01d: 00000000	MI_NOOP                                  1
	0718b021: 00000000	MI_NOOP                                  1
^c
[COLOR="Red"]admin@ubuntu:/media/JPSystem$ tail -20 :0.log.1[/COLOR]
	0ac151f5: 4c3c087f
	0ac151f9: cdc6e666
	0ac151fd: 253ecccc
	0ac15201: 5e3e9249
	0ac15205: 2043c66c
	0ac15209: 80432087
	0ac1520d: 6f3b887f
	0ac15211: 4c3c087f
	0ac15215: cdc6e666
	0ac15219: 193ecccc
	0ac1521d: 663ee747
	0ac15221: 2c43c006
	0ac15225: 80431430
	0ac15229: 6f3b887f
	0ac1522d: 4c3c087f
	0ac15231: 9ac6e666
	0ac15235: 253e9999
	0ac15239: 5e3e9249
	0ac1523d: 2043c66c
	0ac1524

```

---

### Post by karmapia on 2009-02-14
...

---

