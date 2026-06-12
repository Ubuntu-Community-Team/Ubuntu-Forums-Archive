---
title: "[SOLVED] ZSNES error"
date: 2008-11-30
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2008-11-30
Hi,
I cant start ZNES. Here is the output:

```
:~$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7c01558]
/lib/tls/i686/cmov/libc.so.6[0xb7bff680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:05 10841294   /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:05 10841294   /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:05 10841294   /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
0913a000-0918b000 rw-p 0913a000 00:00 0          [heap]
b5e5f000-b698e000 rw-p b5e5f000 00:00 0 
b698e000-b69b0000 r-xp 00000000 08:05 10839691   /usr/lib/libaudiofile.so.0.0.2
b69b0000-b69b3000 rw-p 00021000 08:05 10839691   /usr/lib/libaudiofile.so.0.0.2
b69b3000-b69bc000 r-xp 00000000 08:05 10839848   /usr/lib/libesd.so.0.2.39
b69bc000-b69bd000 r--p 00008000 08:05 10839848   /usr/lib/libesd.so.0.2.39
b69bd000-b69be000 rw-p 00009000 08:05 10839848   /usr/lib/libesd.so.0.2.39
b69be000-b6a0b000 r-xp 00000000 08:05 10839648   /usr/lib/libXt.so.6.0.0
b6a0b000-b6a0f000 rw-p 0004c000 08:05 10839648   /usr/lib/libXt.so.6.0.0
b6a0f000-b6a25000 r-xp 00000000 08:05 10841018   /usr/lib/libaudio.so.2.4
b6a25000-b6a26000 r--p 00015000 08:05 10841018   /usr/lib/libaudio.so.2.4
b6a26000-b6a27000 rw-p 00016000 08:05 10841018   /usr/lib/libaudio.so.2.4
b6a37000-b6a3a000 r-xp 00000000 08:05 17932330   /lib/libcap.so.1.10
b6a3a000-b6a3b000 rw-p 00002000 08:05 17932330   /lib/libcap.so.1.10
b6a3b000-b6a50000 r-xp 00000000 08:05 10839566   /usr/lib/libICE.so.6.3.0
b6a50000-b6a51000 rw-p 00014000 08:05 10839566   /usr/lib/libICE.so.6.3.0
b6a51000-b6a53000 rw-p b6a51000 00:00 0 
b6a53000-b6a5a000 r-xp 00000000 08:05 10839595   /usr/lib/libSM.so.6.0.0
b6a5a000-b6a5b000 r--p 00006000 08:05 10839595   /usr/lib/libSM.so.6.0.0
b6a5b000-b6a5c000 rw-p 00007000 08:05 10839595   /usr/lib/libSM.so.6.0.0
b6a5c000-b6aaa000 r-xp 00000000 08:05 10840379   /usr/lib/libpulse.so.0.4.1
b6aaa000-b6aab000 r--p 0004d000 08:05 10840379   /usr/lib/libpulse.so.0.4.1
b6aab000-b6aac000 rw-p 0004e000 08:05 10840379   /usr/lib/libpulse.so.0.4.1
b6aac000-b6ab8000 r-xp 00000000 08:05 10840377   /usr/lib/libpulse-simple.so.0.0.1
b6ab8000-b6ab9000 r--p 0000b000 08:05 10840377   /usr/lib/libpulse-simple.so.0.0.1
b6ab9000-b6aba000 rw-p 0000c000 08:05 10840377   /usr/lib/libpulse-simple.so.0.0.1
b6aba000-b6ac4000 r-xp 00000000 08:05 17949919   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ac4000-b6ac5000 r--p 00009000 08:05 17949919   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ac5000-b6ac6000 rw-p 0000a000 08:05 17949919   /lib/tls/i686/cmov/libnss_files-2.8.90.so
b6ac6000-b6acf000 r-xp 00000000 08:05 17949923   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6acf000-b6ad0000 r--p 00008000 08:05 17949923   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6ad0000-b6ad1000 rw-p 00009000 08:05 17949923   /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b6ad1000-b6ae6000 r-xp 00000000 08:05 17949913   /lib/tls/i686/cmov/libnsl-2.8.90.so
b6ae6000-b6ae7000 r--p 00014000 08:05 17949913   /lib/tls/i686/cmov/libnsl-2.8.90.so
b6ae7000-b6ae8000 rw-p 00015000 08:05 17949913   /lib/tls/i686/cmov/libnsl-2.8.90.so
b6ae8000-b6aea000 rw-p b6ae8000 00:00 0 
b6aeb000-b6aec000 r-xp 00000000 08:05 10862960   /usr/lib/ao/plugins-2/libesd.so
b6aec000-b6aee000 rw-p 00000000 08:05 10862960   /usr/lib/ao/plugins-2/libesd.so
b6aee000-b6aef000 r-xp 00000000 08:05 10862961   /usr/lib/ao/plugins-2/libnas.so
b6aef000-b6af1000 rw-p 00000000 08:05 10862961   /usr/lib/ao/plugins-2/libnas.so
b6af1000-b6af4000 r-xp 00000000 08:05 10862958   /usr/lib/ao/plugins-2/libalsa09.so
b6af4000-b6af6000 rw-p 00002000 08:05 10862958   /usr/lib/ao/plugins-2/libalsa09.so
b6af6000-b6af8000 r-xp 00000000 08:05 10862962   /usr/lib/ao/plugins-2/liboss.so
b6af8000-b6afa000 rw-p 00001000 08:05 10862962   /usr/lib/ao/plugins-2/liboss.so
b6afa000-b6afd000 rw-p b6afa000 00:00 0 
b6afd000-b6b01000 r-xp 00000000 08:05 10839618   /usr/lib/libXdmcp.so.6.0.0
b6b01000-b6b02000 rw-p 00003000 08:05 10839618   /usr/lib/libXdmcp.so.6.0.0
b6b02000-b6b19000 r-xp 00000000 08:05 10840551   /usr/lib/libxcb.so.1.0.0
b6b19000-b6b1a000 r--p 00016000 08:05 10840551   /usr/lib/libxcb.so.1.0.0
b6b1a000-b6b1b000 rw-p 00017000 08:05 10840551   /usr/lib/libxcb.so.1.0.0
b6b1b000-b6b1c000 r-xp 00000000 08:05 10840549   /usr/lib/libxcb-xlib.so.0.0.0
b6b1c000-b6b1d000 r--p 00000000 08:05 10840549   /usr/lib/libxcb-xlib.so.0.0.0
b6b1d000-b6b1e000 rw-p 00001000 08:05 10840549   /usr/lib/libxcb-xlib.so.0.0.0
b6b1e000-b6b20000 r-xp 00000000 08:05 10839607   /usr/lib/libXau.so.6.0.0
b6b20000-b6b21000 rw-p 00001000 08:05 10839607   /usr/lib/libXau.so.6.0.0
b6b21000-b6b28000 r-xp 00000000 08:05 17949932   /lib/tls/i686/cmov/librt-2.8.90.so
b6b28000-b6b29000 r--p 00007000 08:05 17949932   /lib/tls/i686/cmov/librt-2.8.90.so
b6b29000-b6b2a000 rw-p 00008000 08:05 17949932   /lib/tls/i686/cmov/librt-2.8.90.so
b6b2a000-b6b2b000 rw-p b6b2a000 00:00 0 
b6b2b000-b6c16000 r-xp 00000000 08:05 10839601   /usr/lib/libX11.so.6.2.0
b6c16000-b6c17000 r--p 000ea000 08:05 10839601   /usr/lib/libX11.so.6.2.0
b6c17000-b6c19000 rw-p 000eb000 08:05 10839601   /usr/lib/libX11.so.6.2.0
b6c19000-b6c1a000 rw-p b6c19000 00:00 0 
b6c1a000-b6c27000 r-xp 00000000 08:05 10839622   /usr/lib/libXext.so.6.4.0
b6c27000-b6c29000 rw-p 0000c000 08:05 10839622   /usr/lib/libXext.so.6.4.0
b6c29000-b6c2a000 r-xp 00000000 08:05 10878994   /usr/lib/tls/libnvidia-tls.so.177.80
b6c2a000-b6c2b000 rw-p 00000000 08:05 10878994   /usr/lib/tls/libnvidia-tls.so.177.80
b6c2b000-b77ee000 r-xp 00000000 08:05 10840866   /usr/lib/libGLcore.so.177.80
b77ee000-b7992000 rwxp 00bc3000 08:05 10840866   /usr/lib/libGLcore.so.177.80
b7992000-b799d000 rwxp b7992000 00:00 0 
b799d000-b79b0000 r-xp 00000000 08:05 10839804   /usr/lib/libdirect-1.0.so.0.1.0
b79b0000-b79b1000 r--p 00012000 08:05 10839804   /usr/lib/libdirect-1.0.so.0.1.0
b79b1000-b79b2000 rw-p 00013000 08:05 10839804   /usr/lib/libdirect-1.0.so.0.1.0
b79b2000-b79b9000 r-xp 00000000 08:05 10839882   /usr/lib/libfusion-1.0.so.0.1.0
b79b9000-b79ba000 r--p 00006000 08:05 10839882   /usr/lib/libfusion-1.0.so.0.1.0
b79ba000-b79bb000 rw-p 00007000 08:05 10839882   /usr/lib/libfusion-1.0.so.0.1.0
b79bb000-b79bc000 rw-p b79bb000 00:00 0 
b79bc000-b7a20000 r-xp 00000000 08:05 10839806   /usr/lib/libdirectfb-1.0.so.0.1.0
b7a20000-b7a21000 r--p 00063000 08:05 10839806   /usr/lib/libdirectfb-1.0.so.0.1.0
b7a21000-b7a22000 rw-p 00064000 08:05 10839806   /usr/lib/libdirectfb-1.0.so.0.1.0
b7a22000-b7a24000 r-xp 00000000 08:05 17949908   /lib/tls/i686/cmov/libdl-2.8.90.so
b7a24000-b7a25000 r--p 00001000 08:05 17949908   /lib/tls/i686/cmov/libdl-2.8.90.so
b7a25000-b7a26000 rw-p 00002000 08:05 17949908   /lib/tls/i686/cmov/libdl-2.8.90.so
b7a26000-b7ae9000 r-xp 00000000 08:05 10839681   /usr/lib/libasound.so.2.0.0
b7ae9000-b7aeb000 r--p 000c2000 08:05 10839681   /usr/lib/libasound.so.2.0.0
b7aeb000-b7aee000 rw-p 000c4000 08:05 10839681   /usr/lib/libasound.so.2.0.0
b7aee000-b7b03000 r-xp 00000000 08:05 17949928   /lib/tls/i686/cmov/libpthread-2.8.90.so
b7b03000-b7b04000 r--p 00014000 08:05 17949928   /lib/tls/i686/cmov/libpthread-2.8.90.so
b7b04000-b7b05000 rw-p 00015000 08:05 17949928   /lib/tls/i686/cmov/libpthread-2.8.90.so
b7b05000-b7b07000 rw-p b7b05000 00:00 0 
b7b07000-b7c5f000 r-xp 00000000 08:05 17949902   /lib/tls/i686/cmov/libc-2.8.90.so
b7c5f000-b7c61000 r--p 00158000 08:05 17949902   /lib/tls/i686/cmov/libc-2.8.90.so
b7c61000-b7c62000 rw-p 0015a000 08:05 17949902   /lib/tls/i686/cmov/libc-2.8.90.so
b7c62000-b7c66000 rw-p b7c62000 00:00 0 
b7c66000-b7c73000 r-xp 00000000 08:05 17932350   /lib/libgcc_s.so.1
b7c73000-b7c74000 r--p 0000c000 08:05 17932350   /lib/libgcc_s.so.1
b7c74000-b7c75000 rw-p 0000d000 08:05 17932350   /lib/libgcc_s.so.1
b7c75000-b7c99000 r-xp 00000000 08:05 17949910   /lib/tls/i686/cmov/libm-2.8.90.so
b7c99000-b7c9a000 r--p 00023000 08:05 17949910   /lib/tls/i686/cmov/libm-2.8.90.so
b7c9a000-b7c9b000 rw-p 00024000 08:05 17949910   /lib/tls/i686/cmov/libm-2.8.90.so
b7c9b000-b7d7e000 r-xp 00000000 08:05 10840469   /usr/lib/libstdc++.so.6.0.10
b7d7e000-b7d7f000 ---p 000e3000 08:05 10840469   /usr/lib/libstdc++.so.6.0.10
b7d7f000-b7d83000 r--p 000e3000 08:05 10840469   /usr/lib/libstdc++.so.6.0.10
b7d83000-b7d84000 rw-p 000e7000 08:05 10840469   /usr/lib/libstdc++.so.6.0.10
b7d84000-b7d8a000 rw-p b7d84000 00:00 0 
b7dAborted
```

---

### Post by Chunky Dunk on 2008-11-30
Check out these links:
[http://ubuntuforums.org/showthread.php?t=960649&highlight=zsnes](http://ubuntuforums.org/showthread.php?t=960649&highlight=zsnes)
[http://ubuntuforums.org/showthread.php?t=989539&highlight=zsnes](http://ubuntuforums.org/showthread.php?t=989539&highlight=zsnes)

Edit: The original post I was linking to seems to have disappeared...:confused:

---

### Post by Rytron on 2008-12-01
> **Chunky Dunk said:**
> I replied to your other post: [http://ubuntuforums.org/showthread.php?p=6282110#post6282110](http://ubuntuforums.org/showthread.php?p=6282110#post6282110)

Cheers buudy.

---

### Post by Rytron on 2008-12-14
I've decided to swap over to Snes9Express.

---

### Post by shecky on 2008-12-17
I know this was *implied* in the linked threads, but copy/paste commands are quick and easy for the impatient. You can "fix" this with the Hardy package.
```
wget http://lug.mtu.edu/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2ubuntu1_i386.deb
dpkg -x zsnes_1.510-2ubuntu1_i386.deb zsnes/
sudo cp zsnes/usr/bin/zsnes /usr/local/bin/
```

Point any shortcuts at "/usr/local/bin/zsnes". Probably need Intrepid's zsnes package installed as well, just to meet any dependencies.

---

