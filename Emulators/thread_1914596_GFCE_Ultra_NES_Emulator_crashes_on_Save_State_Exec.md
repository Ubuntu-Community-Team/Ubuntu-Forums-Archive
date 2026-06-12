---
title: "GFCE Ultra NES Emulator crashes on Save State Execution"
date: 2012-01-24
forum: Emulators
---

### Post by Wolfk1d on 2012-01-24
Greetings,

Any one ever had this issue with GFCE Ultra NES emulator.  

I feel like I am almost there I had sound and video issues in 11.10 before i installed libgnomevfs and I installed gnome shell and that seems to fix most everything.  Originaly I couldnt full screen without the emulator bombing and the sound going crazy.

I have no idea how to fix this but when i hit F5 to save the state get the following dump in the terminal.
I can select the state i want to save in with no issue.  

Any help would be greatly appreciated.

```

gfceu message:  Using: /usr/games/fceu
/usr/bin/gfceu:510: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.widgets = gtk.glade.XML(glade_file)
wolfserver@wolfserver:~$ gfceu

(gfceu:5340): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gfceu:5340): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gfceu:5340): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gfceu:5340): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
gfceu message:  Using: /usr/games/fceu
/usr/bin/gfceu:510: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.widgets = gtk.glade.XML(glade_file)
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 0 -opengl 1  "/home/wolfserver/Final Fantasy.nes"

Starting FCE Ultra 0.98.12...
Loading /home/wolfserver/Final Fantasy.nes...

 PRG ROM:   16 x 16KiB
 CHR ROM:    0 x  8KiB
 ROM CRC32:  0xcebd2a31
 ROM MD5:  0x24ae5edf8375162f91a6846d3202e3d6
 Mapper:  1
 Mirroring: Horizontal
 Battery-backed.

Initializing video... Video Mode: 512 x 448 x 32 bpp 

Initializing sound...
 Bits: 16
 Rate: 48000
 Channels: 1
 Byte order: CPU Native
 Buffer size: 1024 sample frames(21.333333 ms)
Initializing video...
 Initializing with OpenGL(Use "-opengl 0" to disable).
 Video Mode: 640 x 480 x 32 bpp full screen
Paletted texture extension not found.  Using slower texture format...Initializing video... Video Mode: 512 x 448 x 32 bpp 
*** buffer overflow detected ***: /usr/games/fceu terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x37)[0x7f4ea1c387f7]
/lib/x86_64-linux-gnu/libc.so.6(+0xf7710)[0x7f4ea1c37710]
/usr/games/fceu[0x41ccbd]
/usr/games/fceu[0x41d820]
/usr/games/fceu[0x4dbba7]
/usr/games/fceu[0x4de883]
/usr/games/fceu[0x4df0c2]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f4ea1b6130d]
/usr/games/fceu[0x402d39]
======= Memory map: ========
00400000-004fa000 r-xp 00000000 08:11 656416                             /usr/games/fceu
006f9000-006fa000 r--p 000f9000 08:11 656416                             /usr/games/fceu
006fa000-00704000 rw-p 000fa000 08:11 656416                             /usr/games/fceu
00704000-008ca000 rw-p 00000000 00:00 0 
0231e000-026d1000 rw-p 00000000 00:00 0                                  [heap]
7f4e97996000-7f4e97997000 ---p 00000000 00:00 0 
7f4e97997000-7f4e98197000 rw-p 00000000 00:00 0 
7f4e98197000-7f4e9c198000 rw-s 00000000 00:12 21653                      /run/shm/pulse-shm-2211133405
7f4e9c198000-7f4e9c19d000 r-xp 00000000 08:11 920150                     /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
7f4e9c19d000-7f4e9c39d000 ---p 00005000 08:11 920150                     /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
7f4e9c39d000-7f4e9c39e000 r--p 00005000 08:11 920150                     /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
7f4e9c39e000-7f4e9c39f000 rw-p 00006000 08:11 920150                     /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_pcm_pulse.so
7f4e9c39f000-7f4e9c3a6000 r--s 00000000 08:11 920610                     /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
7f4e9d4b1000-7f4e9d4c6000 r-xp 00000000 08:11 265681                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f4e9d4c6000-7f4e9d6c5000 ---p 00015000 08:11 265681                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f4e9d6c5000-7f4e9d6c6000 r--p 00014000 08:11 265681                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f4e9d6c6000-7f4e9d6c7000 rw-p 00015000 08:11 265681                     /lib/x86_64-linux-gnu/libgcc_s.so.1
7f4e9d6c7000-7f4e9d6cc000 r-xp 00000000 08:11 663141                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f4e9d6cc000-7f4e9d8cb000 ---p 00005000 08:11 663141                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f4e9d8cb000-7f4e9d8cc000 r--p 00004000 08:11 663141                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f4e9d8cc000-7f4e9d8cd000 rw-p 00005000 08:11 663141                     /usr/lib/x86_64-linux-gnu/libXfixes.so.3.1.0
7f4e9d8cd000-7f4e9d8d6000 r-xp 00000000 08:11 663151                     /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f4e9d8d6000-7f4e9dad6000 ---p 00009000 08:11 663151                     /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f4e9dad6000-7f4e9dad7000 r--p 00009000 08:11 663151                     /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f4e9dad7000-7f4e9dad8000 rw-p 0000a000 08:11 663151                     /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
7f4e9dad8000-7f4e9dae1000 r-xp 00000000 08:11 663133                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f4e9dae1000-7f4e9dce0000 ---p 00009000 08:11 663133                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f4e9dce0000-7f4e9dce1000 r--p 00008000 08:11 663133                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f4e9dce1000-7f4e9dce2000 rw-p 00009000 08:11 663133                     /usr/lib/x86_64-linux-gnu/libXcursor.so.1.0.2
7f4e9dce2000-7f4e9e3c6000 r--p 00000000 08:11 661452                     /usr/lib/locale/locale-archive
7f4e9e3c6000-7f4e9e3d8000 r-xp 00000000 08:11 663139                     /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f4e9e3d8000-7f4e9e5d7000 ---p 00012000 08:11 663139                     /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f4e9e5d7000-7f4e9e5d8000 r--p 00011000 08:11 663139                     /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f4e9e5d8000-7f4e9e5d9000 rw-p 00012000 08:11 663139                     /usr/lib/x86_64-linux-gnu/libXext.so.6.4.0
7f4e9e5d9000-7f4e9e70c000 r-xp 00000000 08:11 663127                     /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f4e9e70c000-7f4e9e90c000 ---p 00133000 08:11 663127                     /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f4e9e90c000-7f4e9e90d000 r--p 00133000 08:11 663127                     /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f4e9e90d000-7f4e9e911000 rw-p 00134000 08:11 663127                     /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
7f4e9e911000-7f4e9e928000 r-xp 00000000 08:11 265722                     /lib/x86_64-linux-gnu/libresolv-2.13.so
7f4e9e928000-7f4e9eb28000 ---p 00017000 08:11 265722                     /lib/x86_64-linux-gnu/libresolv-2.13.so
7f4e9eb28000-7f4e9eb29000 r--p 00017000 08:11 265722                     /lib/x86_64-linux-gnu/libresolv-2.13.so
7f4e9eb29000-7f4e9eb2a000 rw-p 00018000 08:11 265722                     /lib/x86_64-linux-gnu/libresolv-2.13.so
7f4e9eb2a000-7f4e9eb2c000 rw-p 00000000 00:00 0 
7f4e9eb2c000-7f4e9eb32000 r-xp 00000000 08:11 663329                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f4e9eb32000-7f4e9ed31000 ---p 00006000 08:11 663329                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f4e9ed31000-7f4e9ed32000 r--p 00005000 08:11 663329                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f4e9ed32000-7f4e9ed33000 rw-p 00006000 08:11 663329                     /usr/lib/x86_64-linux-gnu/libogg.so.0.7.1
7f4e9ed33000-7f4e9ed5e000 r-xp 00000000 08:11 663411                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f4e9ed5e000-7f4e9ef5d000 ---p 0002b000 08:11 663411                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f4e9ef5d000-7f4e9ef5e000 r--p 0002a000 08:11 663411                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f4e9ef5e000-7f4e9ef5f000 rw-p 0002b000 08:11 663411                     /usr/lib/x86_64-linux-gnu/libvorbis.so.0.4.5
7f4e9ef5f000-7f4e9f212000 r-xp 00000000 08:11 663413                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f4e9f212000-7f4e9f411000 ---p 002b3000 08:11 663413                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f4e9f411000-7f4e9f42d000 r--p 002b2000 08:11 663413                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f4e9f42d000-7f4e9f42e000 rw-p 002ce000 08:11 663413                     /usr/lib/x86_64-linux-gnu/libvorbisenc.so.2.0.8
7f4e9f42e000-7f4e9f476000 r-xp 00000000 08:11 663080                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7f4e9f476000-7f4e9f676000 ---p 00048000 08:11 663080                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7f4e9f676000-7f4e9f677000 r--p 00048000 08:11 663080                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7f4e9f677000-7f4e9f678000 rw-p 00049000 08:11 663080                     /usr/lib/x86_64-linux-gnu/libFLAC.so.8.2.0
7f4e9f678000-7f4e9f68f000 r-xp 00000000 08:11 265695                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7f4e9f68f000-7f4e9f88e000 ---p 00017000 08:11 265695                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7f4e9f88e000-7f4e9f88f000 r--p 00016000 08:11 265695                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7f4e9f88f000-7f4e9f890000 rw-p 00017000 08:11 265695                     /lib/x86_64-linux-gnu/libnsl-2.13.so
7f4e9f890000-7f4e9f892000 rw-p 00000000 00:00 0 
7f4e9f892000-7f4e9f897000 r-xp 00000000 08:11 663137                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f4e9f897000-7f4e9fa96000 ---p 00005000 08:11 663137                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f4e9fa96000-7f4e9fa97000 r--p 00004000 08:11 663137                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f4e9fa97000-7f4e9fa98000 rw-p 00005000 08:11 663137                     /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
7f4e9fa98000-7f4e9fa9a000 r-xp 00000000 08:11 663129                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f4e9fa9a000-7f4e9fc99000 ---p 00002000 08:11 663129                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f4e9fc99000-7f4e9fc9a000 r--p 00001000 08:11 663129                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f4e9fc9a000-7f4e9fc9b000 rw-p 00002000 08:11 663129                     /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
7f4e9fc9b000-7f4e9fca0000 r-xp 00000000 08:11 663163                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f4e9fca0000-7f4e9fe9f000 ---p 00005000 08:11 663163                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f4e9fe9f000-7f4e9fea0000 r--p 00004000 08:11 663163                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f4e9fea0000-7f4e9fea1000 rw-p 00005000 08:11 663163                     /usr/lib/x86_64-linux-gnu/libasyncns.so.0.3.1
7f4e9fea1000-7f4e9ff01000 r-xp 00000000 08:11 663381                     /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.24
7f4e9ff01000-7f4ea0101000 ---p 00060000 08:11 663381                     /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.24
7f4ea0101000-7f4ea0103000 r--p 00060000 08:11 663381                     /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.24
7f4ea0103000-7f4ea0104000 rw-p 00062000 08:11 663381                     /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.24
7f4ea0104000-7f4ea0108000 rw-p 00000000 00:00 0 
7f4ea0108000-7f4ea0110000 r-xp 00000000 08:11 265741                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f4ea0110000-7f4ea030f000 ---p 00008000 08:11 265741                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f4ea030f000-7f4ea0310000 r--p 00007000 08:11 265741                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f4ea0310000-7f4ea0311000 rw-p 00008000 08:11 265741                     /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f4ea0311000-7f4ea032c000 r-xp 00000000 08:11 663425                     /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f4ea032c000-7f4ea052b000 ---p 0001b000 08:11 663425                     /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f4ea052b000-7f4ea052c000 r--p 0001a000 08:11 663425                     /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f4ea052c000-7f4ea052d000 rw-p 0001b000 08:11 663425                     /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
7f4ea052d000-7f4ea0534000 r-xp 00000000 08:11 265724                     /lib/x86_64-linux-gnu/librt-2.13.so
7f4ea0534000-7f4ea0733000 ---p 00007000 08:11 265724                     /lib/x86_64-linux-gnu/librt-2.13.so
7f4ea0733000-7f4ea0734000 r--p 00006000 08:11 265724                     /lib/x86_64-linux-gnu/librt-2.13.so
7f4ea0734000-7f4ea0735000 rw-p 00007000 08:11 265724                     /lib/x86_64-linux-gnu/librt-2.13.so
7f4ea0735000-7f4ea0777000 r-xp 00000000 08:11 265670                     /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f4ea0777000-7f4ea0976000 ---p 00042000 08:11 265670                     /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f4ea0976000-7f4ea0977000 r--p 00041000 08:11 265670                     /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f4ea0977000-7f4ea0978000 rw-p 00042000 08:11 265670                     /lib/x86_64-linux-gnu/libdbus-1.so.3.5.7
7f4ea0978000-7f4ea097f000 r-xp 00000000 08:11 663286                     /usr/lib/x86_64-linux-gnu/libjson.so.0.0.1
7f4ea097f000-7f4ea0b7e000 ---p 00007000 08:11 663286                     /usr/lib/x86_64-linux-gnu/libjson.so.0.0.1
7f4ea0b7e000-7f4ea0b7f000 r--p 00006000 08:11 663286                     /usr/lib/x86_64-linux-gnu/libjson.so.0.0.1
7f4ea0b7f000-7f4ea0b80000 rw-p 00007000 08:11 663286                     /usr/lib/x86_64-linux-gnu/libjson.so.0.0.1
7f4ea0b80000-7f4ea0bdc000 r-xp 00000000 08:11 660700                     /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so
7f4ea0bdc000-7f4ea0ddc000 ---p 0005c000 08:11 660700                     /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so
7f4ea0ddc000-7f4ea0ddd000 r--p 0005c000 08:11 660700                     /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so
7f4ea0ddd000-7f4ea0dde000 rw-p 0005d000 08:11 660700                     /usr/lib/x86_64-linux-gnu/libpulsecommon-1.0.so
7f4ea0dde000-7f4ea0ec3000 r-xp 00000000 08:11 663161                     /usr/lib/x86_64-linux-gnu/libasound.so.2.0.0
7f4ea0ec3000-7f4ea10c2000 ---p 000e5000 08:11 663161                     /usr/lib/x86_64-linux-gnu/libasound.so.2.0.0
7f4ea10c2000-7f4ea10c8000 r--p 000e4000 08:11 663161                     /usr/lib/x86_64-linux-gnu/libasound.so.2.0.0
7f4ea10c8000-7f4ea10c9000 rw-p 000ea000 08:11 663161                     /usr/lib/x86_64-linux-gnu/libasound.so.2.0.0
7f4ea10c9000-7f4ea10e1000 r-xp 00000000 08:11 265720                     /lib/x86_64-linux-gnu/libpthread-2.13.so
7f4ea10e1000-7f4ea12e0000 ---p 00018000 08:11 265720                     /lib/x86_64-linux-gnu/libpthread-2.13.so
7f4ea12e0000-7f4ea12e1000 r--p 00017000 08:11 265720                     /lib/x86_64-linux-gnu/libpthread-2.13.so
7f4ea12e1000-7f4ea12e2000 rw-p 00018000 08:11 265720                     /lib/x86_64-linux-gnu/libpthread-2.13.so
7f4ea12e2000-7f4ea12e6000 rw-p 00000000 00:00 0 
7f4ea12e6000-7f4ea132c000 r-xp 00000000 08:11 660698                     /usr/lib/x86_64-linux-gnu/libpulse.so.0.13.4
7f4ea132c000-7f4ea152b000 ---p 00046000 08:11 660698                     /usr/lib/x86_64-linux-gnu/libpulse.so.0.13.4
7f4ea152b000-7f4ea152c000 r--p 00045000 08:11 660698                     /usr/lib/x86_64-linux-gnu/libpulse.so.0.13.4
7f4ea152c000-7f4ea152d000 rw-p 00046000 08:11 660698                     /usr/lib/x86_64-linux-gnu/libpulse.so.0.13.4
7f4ea152d000-7f4ea1530000 r-xp 00000000 08:11 660699                     /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0.0.3
7f4ea1530000-7f4ea172f000 ---p 00003000 08:11 660699                     /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0.0.3
7f4ea172f000-7f4ea1730000 r--p 00002000 08:11 660699                     /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0.0.3
7f4ea1730000-7f4ea1731000 rw-p 00003000 08:11 660699                     /usr/lib/x86_64-linux-gnu/libpulse-simple.so.0.0.3
7f4ea1731000-7f4ea1733000 r-xp 00000000 08:11 265671                     /lib/x86_64-linux-gnu/libdl-2.13.so
7f4ea1733000-7f4ea1933000 ---p 00002000 08:11 265671                     /lib/x86_64-linux-gnu/libdl-2.13.so
7f4ea1933000-7f4ea1934000 r--p 00002000 08:11 265671                     /lib/x86_64-linux-gnu/libdl-2.13.so
7f4ea1934000-7f4ea1935000 rw-p 00003000 08:11 265671                     /lib/x86_64-linux-gnu/libdl-2.13.so
7f4ea1935000-7f4ea193e000 r-xp 00000000 08:11 654187                     /usr/lib/libalsatoss.so.0.0.0
7f4ea193e000-7f4ea1b3e000 ---p 00009000 08:11 654187                     /usr/lib/libalsatoss.so.0.0.0
7f4ea1b3e000-7f4ea1b3f000 r--p 00009000 08:11 654187                     /usr/lib/libalsatoss.so.0.0.0
7f4ea1b3f000-7f4ea1b40000 rw-p 0000a000 08:11 654187                     /usr/lib/libalsatoss.so.0.0.0
7f4ea1b40000-7f4ea1cd5000 r-xp 00000000 08:11 265660                     /lib/x86_64-linux-gnu/libc-2.13.so
7f4ea1cd5000-7f4ea1ed4000 ---p 00195000 08:11 265660                     /lib/x86_64-linux-gnu/libc-2.13.so
7f4ea1ed4000-7f4ea1ed8000 r--p 00194000 08:11 265660                     /lib/x86_64-linux-gnu/libc-2.13.so
7f4ea1ed8000-7f4ea1ed9000 rw-p 00198000 08:11 265660                     /lib/x86_64-linux-gnu/libc-2.13.so
Signal 6 has been caught and dealt with...

```

---

### Post by Wolfk1d on 2012-01-25
Turns out the emulator currently being developed supported is FCEUX and not FCEU with the GFCE frontend using FCEUX fixed all problems.

---

### Post by genosias on 2012-12-25
fceux is just horribly bugged here (ubuntu 12.10) he crash everytimes.

---

