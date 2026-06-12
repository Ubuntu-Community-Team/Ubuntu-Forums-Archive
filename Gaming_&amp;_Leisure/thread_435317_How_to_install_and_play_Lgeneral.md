---
title: "How to install and play Lgeneral"
date: 2007-05-06
forum: Gaming &amp; Leisure
---

### Post by flewis7777 on 2007-05-06
I had such a hard time installing Lgeneral but I
found that it can be installed. Some people
are having trouble with how the menus work. Lgeneral
needs a right-mouse-click to open the pop-up game
menu. I looked for a traditional window menu and
at first I thought I was out of luck. Just right click
the first two screens and right click again and choose load
camplaign from the pop-up menu.

To install lgeneral you have to download the 
pg-data file as well as the lgeneral file. 

I got the pg-data file from 
[http://lgames.sourceforge.net/index.php?project=LGeneral](http://lgames.sourceforge.net/index.php?project=LGeneral)
Or google "lgames" or google "lgeneral".

In Synaptic if you search for lgeneral,
lgc-pg will also appear. Download and install both. lgc-pg
is used to convert the pg-data files so lgeneral can work.

I installed the pg-data file to my home directory
in a folder called Lgeneral.

In the pg-data folder I had to convert to upper case 
five files so lgc-pg could find them: scenstat.bin, 
tacicons.shp, tacmap.shp explode.shp, and flags.shp. 
That's it just five files not everything. Just rename to UPPERCASE NAME.

Next run from command line sudo lgc-pg -s ~/<path to where you put pg-data>/pg-data -d /usr/share/games/lgeneral.

I used Synaptic and Synaptic put lgeneral in /usr/share/games but since I had to
download pg-data manually you have to put your own path in.

That's it. Lgeneral works fine.
:popcorn:

---

### Post by loukasmaki on 2007-05-25
GREAT! now I atleast can play scenarios. But isn't there supposed to be a campaign?

---

### Post by joao82 on 2007-06-23
Thank you. this was really helpful.

---

### Post by bmm on 2008-08-12
There are also unofficial debian packages to use. Using google you can find [http://log.logfish.net/node/32]("http://log.logfish.net/node/32")

---

### Post by yeehi on 2008-11-26
I tried changing the paths to my own and ran that line. No new files or folders appeared in my LGeneral directory. When I tried to manually copy to /usr/share/games/lgeneral using sudo, I get a permission denied error message...

The game runs, but there are no scenarios or campaigns...

---

### Post by Mike Bates on 2009-04-03
Instead of entering:
sudo lgc-pg -s ~/<path to where you put pg-data>/pg-data -d /usr/share/games/lgeneral

try either:
sudo lgc-pg -s /<path to where you put pg-data>/pg-data -d /usr/share/games/lgeneral

or leave out the <username/home> part. I found mine had tried to access:

/mike/home/mike/home/Lgeneral......

Hope this helps

Mike

---

### Post by LEDominator on 2009-09-23
Hello all,

I was able to install lgeneral and everything but got hung up on the conversion part.  I get this error

> root@porter-2-4-2T:/home/tniblett/Desktop/lgeneral/pg-data# lgc-pg -s /home/tniblett/Desktop/lgeneral/pg-data -d /usr/local/share/games/lgeneral
LGeneral Converter for Panzer General (DOS version) v1.2beta-13
Copyright 2002-2005 Michael Speck
Released under GNU GPL
---
Settings:
  Source: /home/tniblett/Desktop/lgeneral/pg-data
  Destination: /usr/local/share/games/lgeneral
  Use Individual Palettes
Converting:
  nation database...
  nation flag graphics...
  unit data base...
overwrite flags of StuGIIIb to : artillery&#65533;suppr_fire
Jadgpanzer 38 -> Jagdpanzer 38		[correct spelling]
overwrite flags of StuG IV to : artillery&#65533;suppr_fire
Jadgpz IV/48 -> Jagdpz IV/48		[correct spelling]
Jadgpz IV/70 -> Jagdpz IV/70		[correct spelling]
JadgPanther -> JagdPanther		[correct spelling]
JadgTiger -> JagdTiger		[correct spelling]
ST BT-5 gets initiative bonus +3
ST BT-7 gets initiative bonus +3
ST T-28M1 gets initiative bonus +3
ST T-34/40 gets initiative bonus +3
ST T-34/41 gets initiative bonus +3
ST T-34/43 gets initiative bonus +3
ST T-34/85 gets initiative bonus +3
ST T-70 gets initiative bonus +3
ST T-60 gets initiative bonus +3
ST T-40 gets initiative bonus +3
ST KV-1/39 gets initiative bonus +3
ST KV-1/41 gets initiative bonus +3
ST KV-1/42 gets initiative bonus +3
ST KV-2 gets initiative bonus +3
ST KV-85 gets initiative bonus +3
ST IS-2 gets initiative bonus +3
overwrite flags of IT Sem M-40 to : artillery&#65533;suppr_fire
overwrite flags of IT Sem M-42M to : artillery&#65533;suppr_fire
  unit graphics...
  terrain database...
  terrain graphics...
  maps...
  scenarios...
/usr/local/share/games/lgeneral/scenarios/pg/Poland: access denied
*** glibc detected *** lgc-pg: double free or corruption (!prev): 0x09b2de68 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7f1e604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb7f205b6]
/lib/tls/i686/cmov/libc.so.6(fclose+0x144)[0xb7f0dfe4]
lgc-pg[0x80513b4]
lgc-pg[0x8049852]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7ec5775]
lgc-pg[0x8049231]
======= Memory map: ========
08048000-08057000 r-xp 00000000 08:03 1856532    /usr/local/bin/lgc-pg
08057000-08058000 r--p 0000e000 08:03 1856532    /usr/local/bin/lgc-pg
08058000-0805a000 rw-p 0000f000 08:03 1856532    /usr/local/bin/lgc-pg
0805a000-0807c000 rw-p 0805a000 00:00 0 
09b02000-09be1000 rw-p 09b02000 00:00 0          [heap]
b6d00000-b6d21000 rw-p b6d00000 00:00 0 
b6d21000-b6e00000 ---p b6d21000 00:00 0 
b6e4d000-b6e4e000 ---p b6e4d000 00:00 0 
b6e4e000-b764e000 rw-p b6e4e000 00:00 0 
b764e000-b7688000 rw-p b7688000 00:00 0 
b7707000-b7714000 r-xp 00000000 08:03 596913     /lib/libgcc_s.so.1
b7714000-b7715000 r--p 0000c000 08:03 596913     /lib/libgcc_s.so.1
b7715000-b7716000 rw-p 0000d000 08:03 596913     /lib/libgcc_s.so.1
b7724000-b7728000 r-xp 00000000 08:03 1775742    /usr/lib/libXfixes.so.3.1.0
b7728000-b7729000 rw-p 00003000 08:03 1775742    /usr/lib/libXfixes.so.3.1.0
b7729000-b7731000 r-xp 00000000 08:03 1775762    /usr/lib/libXrender.so.1.3.0
b7731000-b7732000 r--p 00007000 08:03 1775762    /usr/lib/libXrender.so.1.3.0
b7732000-b7733000 rw-p 00008000 08:03 1775762    /usr/lib/libXrender.so.1.3.0
b7733000-b773b000 r-xp 00000000 08:03 1775734    /usr/lib/libXcursor.so.1.0.2
b773b000-b773c000 rw-p 00007000 08:03 1775734    /usr/lib/libXcursor.so.1.0.2
b7748000-b7749000 rw-p b7748000 00:00 0 
b7749000-b774a000 rw-s 00000000 00:09 2064409    /SYSV00000000 (deleted)
b774a000-b7789000 r--p 00000000 08:03 1807742    /usr/lib/locale/en_US.utf8/LC_CTYPE
b7789000-b778a000 r--p 00000000 08:03 1807747    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b778a000-b778b000 r--p 00000000 08:03 1807750    /usr/lib/locale/en_US.utf8/LC_TIME
b778b000-b7876000 r--p 00000000 08:03 1807741    /usr/lib/locale/en_US.utf8/LC_COLLATE
b7876000-b7877000 r--p 00000000 08:03 1807745    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7877000-b7885000 r-xp 00000000 08:03 1775740    /usr/lib/libXext.so.6.4.0
b7885000-b7886000 r--p 0000d000 08:03 1775740    /usr/lib/libXext.so.6.4.0
b7886000-b7887000 rw-p 0000e000 08:03 1775740    /usr/lib/libXext.so.6.4.0
b7887000-b788a000 rw-p b7887000 00:00 0 
b788a000-b788e000 r-xp 00000000 08:03 1775738    /usr/lib/libXdmcp.so.6.0.0
b788e000-b788f000 rw-p 00003000 08:03 1775738    /usr/lib/libXdmcp.so.6.0.0
b788f000-b7891000 r-xp 00000000 08:03 1775727    /usr/lib/libXau.so.6.0.0
b7891000-b7892000 r--p 00001000 08:03 1775727    /usr/lib/libXau.so.6.0.0
b7892000-b7893000 rw-p 00002000 08:03 1775727    /usr/lib/libXau.so.6.0.0
b7893000-b7897000 r-xp 00000000 08:03 596883     /lib/libattr.so.1.1.0
b7897000-b7898000 r--p 00003000 08:03 596883     /lib/libattr.so.1.1.0
b7898000-b7899000 rw-p 00004000 08:03 596883     /lib/libattr.so.1.1.0
b7899000-b78b1000 r-xp 00000000 08:03 1775629    /usr/lib/libxcb.so.1.1.0
b78b1000-b78b2000 r--p 00017000 08:03 1775629    /usr/lib/libxcb.so.1.1.0
b78b2000-b78b3000 rw-p 00018000 08:03 1775629    /usr/lib/libxcb.so.1.1.0
b78b3000-b78b6000 r-xp 00000000 08:03 597002     /lib/libuuid.so.1.2
b78b6000-b78b7000 r--p 00002000 08:03 597002     /lib/libuuid.so.1.2
b78b7000-b78b8000 rw-p 00003000 08:03 597002     /lib/libuuid.so.1.2
b78b8000-b78b9000 rw-p b78b8000 00:00 0 
b78b9000-b78cd000 r-xp 00000000 08:03 597009     /lib/libz.so.1.2.3.3
b78cd000-b78ce000 r--p 00013000 08:03 597009     /lib/libz.so.1.2.3.3
b78ce000-b78cf000 rw-p 00014000 08:03 597009     /lib/libz.so.1.2.3.3
b78cf000-b7909000 r-xp 00000000 08:03 596930     /lib/libncursesw.so.5.7
b7909000-b790a000 ---p 0003a000 08:03 596930     /lib/libncursesw.so.5.7
b790a000-b790c000 r--p 0003a000 08:03 596930     /lib/libncursesw.so.5.7
b790c000-b790d000 rw-p 0003c000 08:03 596930     /lib/libncursesw.so.5.7
b790d000-b7912000 r-xp 00000000 08:03 1776146    /usr/lib/libgpm.so.2.0.0
b7912000-b7913000 r--p 00004000 08:03 1776146    /usr/lib/libgpm.so.2.0.0
b7913000-b7914000 rw-p 00005000 08:03 1776146    /usr/lib/libgpm.so.2.0.0
b7914000-b79af000 r-xp 00000000 08:03 596980     /lib/libslang.so.2.1.3
b79af000-b79b2000 r--p 0009a000 08:03 596980     /lib/libslang.so.2.1.3
b79b2000-b79bf000 rw-p 0009d000 08:03 596980     /lib/libslang.so.2.1.3
b79bf000-b79f5000 rw-p b79bf000 00:00 0 
b79f5000-b7a24000 r-xp 00000000 08:03 596928     /lib/libncurses.so.5.7
b7a24000-b7a26000 r--p 0002e000 08:03 596928     /lib/libncurses.so.5.7
b7a26000-b7a27000 rw-p 00030000 08:03 596928     /lib/libncurses.so.5.7
b7a27000-b7a28000 rw-p b7a27000 00:00 0 
b7a28000-b7a2d000 r-xp 00000000 08:03 1776026    /usr/lib/libgdbm.so.3.0.0
b7a2d000-b7a2e000 r--p 00004000 08:03 1776026    /usr/lib/libgdbm.so.3.0.0
b7a2e000-b7a2f000 rw-p 00005000 08:03 1776026    /usr/lib/libgdbm.so.3.0.0
b7a2f000-b7a32000 r-xp 00000000 08:03 596894     /lib/libcap.so.2.11
b7a32000-b7a33000 r--p 00002000 08:03 596894     /lib/libcap.so.2.11
b7a33000-b7a34000 rw-p 00003000 08:03 596894     /lib/libcap.so.2.11
b7a34000-b7b1e000 r-xp 00000000 08:03 1775721    /usr/lib/libX11.so.6.2.0
b7b1e000-b7b1f000 ---p 000ea000 08:03 1775721    /usr/lib/libX11.so.6.2.0
b7b1f000-b7b20000 r--p 000ea000 08:03 1775721    /usr/lib/libX11.so.6.2.0
b7b20000-b7b22000 rw-p 000eb000 08:03 1775721    /usr/lib/libX11.so.6.2.0
b7b22000-b7b23000 rw-p b7b22000 00:00 0 
b7b23000-b7b38000 r-xp 00000000 08:03 1775689    /usr/lib/libICE.so.6.3.0
b7b38000-b7b39000 rw-p 00014000 08:03 1775689    /usr/lib/libICE.so.6.3.0
b7b39000-b7b3b000 rw-p b7b39000 00:00 0 
b7b3b000-b7b42000 r-xp 00000000 08:03 1775719    /usr/lib/libSM.so.6.0.0
b7b42000-b7b43000 r--p 00006000 08:03 1775719    /usr/lib/libSM.so.6.0.0
b7b43000-b7b44000 rw-p 00007000 08:03 1775719    /usr/lib/libSM.so.6.0.0
b7b44000-b7b45000 rw-p b7b44000 00:00 0 
b7b45000-b7b4c000 r-xp 00000000 08:03 614114     /lib/tls/i686/cmov/librt-2.9.so
b7b4c000-b7b4d000 r--p 00006000 08:03 614114     /lib/tls/i686/cmov/librt-2.9.so
b7b4d000-b7b4e000 rw-p 00007000 08:03 614114     /lib/tls/i686/cmov/librt-2.9.so
b7b4e000-b7b63000 r-xp 00000000 08:03 614112     /lib/tls/i686/cmov/libpthread-2.9.so
b7b63000-b7b64000 r--p 00014000 08:03 614112     /lib/tls/i686/cmov/libpthread-2.9.so
b7b64000-b7b65000 rw-p 00015000 08:03 614112     /lib/tls/i686/cmov/libpthread-2.9.so
b7b65000-b7b67000 rw-p b7b65000 00:00 0 
b7b67000-b7b83000 r-xp 00000000 08:03 1775841    /usr/lib/libcaca.so.0.99.16
b7b83000-b7b84000 r--p 0001b000 08:03 1775841    /usr/lib/libcaca.so.0.99.16
b7b84000-b7c0b000 rw-p 0001c000 08:03 1775841    /usr/lib/libcaca.so.0.99.16
b7c0b000-b7c0f000 rw-p b7c0b000 00:00 0 
b7c0f000-b7c27000 r-xp 00000000 08:03 1775782    /usr/lib/libaa.so.1.0.4
b7c27000-b7c28000 r--p 00018000 08:03 1775782    /usr/lib/libaa.so.1.0.4
b7c28000-b7c29000 rw-p 00019000 08:03 1775782    /usr/lib/libaa.so.1.0.4
b7c29000-b7c2b000 rw-p b7c29000 00:00 0 
b7c2b000-b7c3e000 r-xp 00000000 08:03 1775919    /usr/lib/libdirect-1.0.so.0.1.0
b7c3e000-b7c3f000 r--p 00012000 08:03 1775919    /usr/lib/libdirect-1.0.so.0.1.0
b7c3f000-b7c40000 rw-p 00013000 08:03 1775919    /usr/lib/libdirect-1.0.so.0.1.0
b7c40000-b7c41000 rw-p b7c40000 00:00 0 
b7c41000-b7c48000 r-xp 00000000 08:03 1776003    /usr/lib/libfusion-1.0.so.0.1.0
b7c48000-b7c49000 r--p 00006000 08:03 1776003    /usr/lib/libfusion-1.0.so.0.1.0
b7c49000-b7c4a000 rw-p 00007000 08:03 1776003    /usr/lib/libfusion-1.0.so.0.1.0
b7c4a000-b7cae000 r-xp 00000000 08:03 1775921    /usr/lib/libdirectfb-1.0.so.0.1.0
b7cae000-b7caf000 r--p 00063000 08:03 1775921    /usr/lib/libdirectfb-1.0.so.0.1.0
b7caf000-b7cb0000 rw-p 00064000 08:03 1775921    /usr/lib/libdirectfb-1.0.so.0.1.0
b7cb0000-b7cff000 r-xp 00000000 08:03 1775766    /usr/lib/libXt.so.6.0.0
b7cff000-b7d00000 r--p 0004f000 08:03 1775766    /usr/lib/libXt.so.6.0.0
b7d00000-b7d03000 rw-p 00050000 08:03 1775766    /usr/lib/libXt.so.6.0.0
b7d03000-b7d19000 r-xp 00000000 08:03 1776506    /usr/lib/libaudio.so.2.4
b7d19000-b7d1a000 r--p 00015000 08:03 1776506    /usr/lib/libaudio.so.2.4
b7d1a000-b7d1b000 rw-p 00016000 08:03 1776506    /usr/lib/libaudio.so.2.4
b7d1b000-b7d78000 r-xp 00000000 08:03 1775293    /usr/lib/libpulse.so.0.7.1
b7d78000-b7d79000 r--p 0005c000 08:03 1775293    /usr/lib/libpulse.so.0.7.1
b7d79000-b7d7a000 rw-p 0005d000 08:03 1775293    /usr/lib/libpulse.so.0.7.1
b7d7a000-b7d89000 r-xp 00000Aborted

if it helps I am using Ubuntu 9.04 NBR on an Eee PC 1000H

Any help would be very much appreciated!

---

### Post by LEDominator on 2009-10-07
anyone?

---

### Post by Ivkosky on 2010-06-24
Hi

Could anyone help me? I did exactly what flewis7777 wrote, but I got this after running his command:
> LGeneral Converter for Panzer General (DOS version) v0.32
Copyright 2002 Michael Speck
Released under GNU GPL
---
Settings:
  Source: /root/home/ivkosky/Hry/pg-data
  Destination: /usr/share/games/lgeneral
  Use Individual Palettes
Converting:
  nation database...
  nation flag graphics...
/root/home/ivkosky/Hry/pg-data/FLAGS.SHP: file not found


But I do have FLAGS.SHP there... I would love to play good old PG once again... :(

**EDIT:** Problem solved by following this guide:
[http://ubuntuforums.org/showthread.php?t=86931](http://ubuntuforums.org/showthread.php?t=86931)

---

