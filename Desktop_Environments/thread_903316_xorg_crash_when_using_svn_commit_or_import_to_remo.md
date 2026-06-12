---
title: "xorg crash when using svn commit or import to remote server"
date: 2008-08-28
forum: Desktop Environments
---

### Post by JacobSingh on 2008-08-28
Okay, I know this is totally bizarre, like when I pet my dog, the refrigerator explodes, but I've seen it happen many times, and I'm totally convinced.

[SIZE="6"]Environment:[/SIZE]
Hardy Heron 8.04
Thinkpad t60p
LSCPI (relevant bits):
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


[SIZE="6"]Steps to reproduce (for me):[/SIZE]
*Doesn't always happen, and the same thing can happen when not uploading via SVN, but this seems to trigger it about 80% of the time.

1. Use compiz (doesn't happen in metacity)
2. run an svn ci or svn import, doesn't really matter, but it seems like the longer I use svn to upload data to a server, the greater the chance of bailing.
3. X server crashes.  It sometimes restarts, sometimes does not.  If I move to tty1 and try to gdm restart, it will totally hang the computer.  Cannot access any interface gfx or terminal.

[SIZE="6"]Logs:[/SIZE]

[SIZE="5"]X11[/SIZE]

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7fd9420]
2: /usr/lib/xorg/modules//libxaa.so [0xb76846dd]
3: /usr/bin/X [0x8172e24]
4: /usr/bin/X(CompositeGlyphs+0x9a) [0x815a36a]
5: /usr/bin/X [0x8161d29]
6: /usr/bin/X [0x815d085]
7: /usr/bin/X [0x81506ee]
8: /usr/bin/X(Dispatch+0x2cf) [0x808d8df]
9: /usr/bin/X(main+0x48b) [0x807471b]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d65450]
11: /usr/bin/X(FontFileCompleteXLFD+0x201) [0x8073a91]

Fatal server error:
Caught signal 11.  Server aborting

(II) AIGLX: Suspending AIGLX clients for VT switch

[SIZE="5"]syslog:[/SIZE]

Aug 28 15:57:14 jacob-laptop gdm[8435]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0


I'm not sure, but it seems this is also part of the problem (from dmesg):

[  445.501528] [fglrx] interrupt source 10000000 successfully disabled!
[  445.501534] [fglrx] enable ID = 0x00000000
[  445.501536] [fglrx] Receive disable interrupt message with irqEnableMask: 10000000; dwIRQEnableId: 00000008
[  448.575392] [fglrx] PCIe has already been initialized. Reinitializing ...
[  448.594535] [fglrx] Reserve Block - 0 offset =  0Xfffb000 length = 0X5000
[  448.594540] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[  448.594543] [fglrx] Reserve Block - 2 offset =  0Xffbb000 length = 0X40000
[  448.635483] [fglrx] interrupt source 10000000 successfully enabled
[  448.635489] [fglrx] enable ID = 0x00000008
[  448.635498] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000


I'm sure everyone is just going to say I'm a looney, but I just lost an hour of work, so I've got to post something.

Best,
Jacob

---

