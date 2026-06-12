---
title: "reverse vnc Xresources problem"
date: 2008-02-03
forum: Desktop Environments
---

### Post by pdc124 on 2008-02-03
1 want to see a gutsy  desktop on another linux (gentoo FWIW) machine 
the gentoo machine starts vncviewer -listen which does this 

paul@gravity ~ $ vncviewer -listen
vncviewer -listen: Listening on port 5500
vncviewer -listen: Command line errors are not reported until a connection comes in.

and I can telnet to the port 
msc@msc:$ telnet 192.168.0.201 5500
Trying 192.168.0.201...
Connected to 192.168.0.201.
Escape character is '^]'.
                                           

 and when I try to connect this happens on gutsy 
msc@msc:~$ vncconnect -display :1  192.168.0.201
*** glibc detected *** Xtightvnc: double free or corruption (out): 0x08224778 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7e5cd65]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7e60800]
Xtightvnc(ChangeWindowProperty+0x268)[0x8082e88]
Xtightvnc(ProcChangeProperty+0x151)[0x8083091]
Xtightvnc(Dispatch+0x119)[0x8077ff9]
Xtightvnc(main+0x7b4)[0x8060b24]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7e09050]
Xtightvnc[0x8060051]
======= Memory map: ========
08048000-0817f000 r-xp 00000000 03:01 807544     /usr/bin/Xtightvnc
0817f000-08186000 rw-p 00136000 03:01 807544     /usr/bin/Xtightvnc
08186000-08242000 rw-p 08186000 00:00 0          [heap]
b7900000-b7921000 rw-p b7900000 00:00 0
b7921000-b7a00000 ---p b7921000 00:00 0
b7a9a000-b7aa4000 r-xp 00000000 03:01 538574     /lib/libgcc_s.so.1
b7aa4000-b7aa5000 rw-p 0000a000 03:01 538574     /lib/libgcc_s.so.1
b7ab4000-b7ae5000 rw-p b7ab4000 00:00 0
b7ae9000-b7aec000 rw-p b7ae9000 00:00 0
b7af1000-b7df3000 rw-p b7af1000 00:00 0
b7df3000-b7f37000 r-xp 00000000 03:01 538581     /lib/tls/i686/cmov/libc-2.6.1.so
b7f37000-b7f38000 r--p 00143000 03:01 538581     /lib/tls/i686/cmov/libc-2.6.1.so
b7f38000-b7f3a000 rw-p 00144000 03:01 538581     /lib/tls/i686/cmov/libc-2.6.1.so
b7f3a000-b7f3d000 rw-p b7f3a000 00:00 0
b7f3d000-b7f5c000 r-xp 00000000 03:01 804233     /usr/lib/libjpeg.so.62.0.0
b7f5c000-b7f5d000 rw-p 0001e000 03:01 804233     /usr/lib/libjpeg.so.62.0.0
b7f5d000-b7f5f000 r-xp 00000000 03:01 538584     /lib/tls/i686/cmov/libdl-2.6.1.so
b7f5f000-b7f61000 rw-p 00001000 03:01 538584     /lib/tls/i686/cmov/libdl-2.6.1.so
b7f61000-b7f62000 rw-p b7f61000 00:00 0
b7f62000-b7f85000 r-xp 00000000 03:01 538585     /lib/tls/i686/cmov/libm-2.6.1.so
b7f85000-b7f87000 rw-p 00023000 03:01 538585     /lib/tls/i686/cmov/libm-2.6.1.so
b7f87000-b7f9b000 r-xp 00000000 03:01 801774     /usr/lib/libz.so.1.2.3.3
b7f9b000-b7f9c000 rw-p 00013000 03:01 801774     /usr/lib/libz.so.1.2.3.3
b7f9c000-b7fa5000 rw-p b7f9c000 00:00 0
b7fa6000-b7fad000 rw-p b7fa6000 00:00 0
b7fad000-b7fc7000 r-xp 00000000 03:01 541182     /lib/ld-2.6.1.so
b7fc7000-b7fc9000 rw-p 00019000 03:01 541182     /lib/ld-2.6.1.so
bfd68000-bfd7e000 rw-p bfd68000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
X connection to :1.0 broken (explicit kill or server shutdown).
msc@msc:~$                  


the log file is this 

msc@msc:~$ cat  /home/msc/.vnc/msc:1.log
03/02/08 14:59:25 Xvnc version 3.3.tight1.2.9
03/02/08 14:59:25 Copyright (C) 1999 AT&T Laboratories Cambridge.
03/02/08 14:59:25 Copyright (C) 2000-2002 Constantin Kaplinsky.
03/02/08 14:59:25 All Rights Reserved.
03/02/08 14:59:25 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
03/02/08 14:59:25 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
03/02/08 14:59:25 Desktop name 'X' (msc:1)
03/02/08 14:59:25 Protocol version supported 3.3
03/02/08 14:59:25 Listening for VNC connections on TCP port 5901
03/02/08 14:59:25 Listening for HTTP connections on TCP port 5801
03/02/08 14:59:25   URL [http://msc:5801](http://msc:5801)
Font directory '/usr/X11R6/lib/X11/fonts/Type1/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/Speedo/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/misc/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/75dpi/' not found - ignoring
Font directory '/usr/X11R6/lib/X11/fonts/100dpi/' not found - ignoring
xrdb: No such file or directory
xrdb: can't open file '/home/msc/.Xresources'
Option --login is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new --window-with-profile option

03/02/08 14:59:31 Making connection to client on host 192.168.0.201 port 5500
Window manager warning: Log level 32: could not find XKB extension.
Window manager warning: Fatal IO error 104 (Connection reset by peer) on display ':1'.
gnome-terminal: Fatal IO error 104 (Connection reset by peer) on X server :1.0.
msc@msc:~$                              

and the gentoo box does this 

ul@gravity ~ $ vncviewer -listen
vncviewer -listen: Listening on port 5500
vncviewer -listen: Command line errors are not reported until a connection comes in.
Connected to RFB server, using protocol version 3.3
vncviewer: read: Connection reset by peer
                                                   
so the problem is at the gutsy end. 

But what ? 
( FWIW an alternative Command line installation and kdebase has been added, and running a kde desktop .)

---

