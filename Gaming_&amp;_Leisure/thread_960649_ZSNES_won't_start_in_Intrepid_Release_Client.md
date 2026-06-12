---
title: "ZSNES won't start in Intrepid Release Client"
date: 2008-10-27
forum: Gaming &amp; Leisure
---

### Post by 1337yit on 2008-10-27
When I try to start ZSNES from both the Apps menu or terminal, this happens

```
 zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7ced558]
/lib/tls/i686/cmov/libc.so.6[0xb7ceb680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:05 333389     /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:05 333389     /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:05 333389     /usr/bin/zsnes
08343000-08941000 rw-p 08343000 00:00 0          [heap]
b6ba7000-b76d6000 rw-p b6ba7000 00:00 0 
b76d6000-b7723000 r-xp 00000000 08:05 334618     /usr/lib/libXt.so.6.0.0
b7723000-b7727000 rw-p 0004c000 08:05 334618     /usr/lib/libXt.so.6.0.0
b7727000-b773d000 r-xp 00000000 08:05 333577     /usr/lib/libaudio.so.2.4
b773d000-b773e000 r--p 00015000 08:05 333577     /usr/lib/libaudio.so.2.4
b773e000-b773f000 rw-p 00016000 08:05 333577     /usr/lib/libaudio.so.2.4
b7753000-b7775000 r-xp 00000000 08:05 334659     /usr/lib/libaudiofile.so.0.0.2
b7775000-b7778000 rw-p 00021000 08:05 334659     /usr/lib/libaudiofile.so.0.0.2
b7785000-b7787000 r-xp 00000000 08:05 357639     /usr/lib/ao/plugins-2/liboss.so
b7787000-b7789000 rw-p 00001000 08:05 357639     /usr/lib/ao/plugins-2/liboss.so
b7789000-b778a000 r-xp 00000000 08:05 357638     /usr/lib/ao/plugins-2/libnas.so
b778a000-b778c000 rw-p 00000000 08:05 357638     /usr/lib/ao/plugins-2/libnas.so
b778c000-b778f000 r-xp 00000000 08:05 170730     /lib/libcap.so.1.10
b778f000-b7790000 rw-p 00002000 08:05 170730     /lib/libcap.so.1.10
b7790000-b77a5000 r-xp 00000000 08:05 334541     /usr/lib/libICE.so.6.3.0
b77a5000-b77a6000 rw-p 00014000 08:05 334541     /usr/lib/libICE.so.6.3.0
b77a6000-b77a8000 rw-p b77a6000 00:00 0 
b77a8000-b77af000 r-xp 00000000 08:05 333395     /usr/lib/libSM.so.6.0.0
b77af000-b77b0000 r--p 00006000 08:05 333395     /usr/lib/libSM.so.6.0.0
b77b0000-b77b1000 rw-p 00007000 08:05 333395     /usr/lib/libSM.so.6.0.0
b77b1000-b77ff000 r-xp 00000000 08:05 334348     /usr/lib/libpulse.so.0.4.1
b77ff000-b7800000 r--p 0004d000 08:05 334348     /usr/lib/libpulse.so.0.4.1
b7800000-b7801000 rw-p 0004e000 08:05 334348     /usr/lib/libpulse.so.0.4.1
b7801000-b780d000 r-xp 00000000 08:05 335489     /usr/lib/libpulse-simple.so.0.0.1
b780d000-b780e000 r--p 0000b000 08:05 335489     /usr/lib/libpulse-simple.so.0.0.1
b780e000-b780f000 rw-p 0000c000 08:05 335489     /usr/lib/libpulse-simple.so.0.0.1
b780f000-b7837000 r-xp 00000000 08:05 170763     /lib/libpcre.so.3.12.1
b7837000-b7838000 r--p 00027000 08:05 170763     /lib/libpcre.so.3.12.1
b7838000-b7839000 rw-p 00028000 08:05 170763     /lib/libpcre.so.3.12.1
b7839000-b78ee000 r-xp 00000000 08:05 335191     /usr/lib/libglib-2.0.so.0.1800.2
b78ee000-b78ef000 r--p 000b4000 08:05 335191     /usr/lib/libglib-2.0.so.0.1800.2
b78ef000-b78f0000 rw-p 000b5000 08:05 335191     /usr/lib/libglib-2.0.so.0.1800.2
b78f0000-b78f4000 r-xp 00000000 08:05 335203     /usr/lib/libgthread-2.0.so.0.1800.2
b78f4000-b78f5000 r--p 00003000 08:05 335203     /usr/lib/libgthread-2.0.so.0.1800.2
b78f5000-b78f6000 rw-p 00004000 08:05 335203     /usr/lib/libgthread-2.0.so.0.1800.2
b78f7000-b7900000 r-xp 00000000 08:05 336768     /usr/lib/libesd.so.0.2.39
b7900000-b7901000 r--p 00008000 08:05 336768     /usr/lib/libesd.so.0.2.39
b7901000-b7902000 rw-p 00009000 08:05 336768     /usr/lib/libesd.so.0.2.39
b7902000-b7903000 r-xp 00000000 08:05 357637     /usr/lib/ao/plugins-2/libesd.so
b7903000-b7905000 rw-p 00000000 08:05 357637     /usr/lib/ao/plugins-2/libesd.so
b7905000-b7908000 r-xp 00000000 08:05 357635     /usr/lib/ao/plugins-2/libalsa09.so
b7908000-b790a000 rw-p 00002000 08:05 357635     /usr/lib/ao/plugins-2/libalsa09.so
b790a000-b7914000 r-xp 00000000 08:05 187940     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7914000-b7915000 r--p 00009000 08:05 187940     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7915000-b7916000 rw-p 0000a000 08:05 187940     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7916000-b791f000 r-xp 00000000 08:05 187942     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b791f000-b7920000 r--p 00008000 08:05 187942     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7920000-b7921000 rw-p 00009000 08:05 187942     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b7921000-b7936000 r-xp 00000000 08:05 187937     /lib/tls/i686/cmov/libnsl-2.8.90.so
b7936000-b7937000 r--p 00014000 08:05 187937     /lib/tls/i686/cmov/libnsl-2.8.90.so
b7937000-b7938000 rw-p 00015000 08:05 187937     /lib/tls/i686/cmov/libnsl-2.8.90.so
b7938000-b793a000 rw-p b7938000 00:00 0 
b793a000-b7941000 r-xp 00000000 08:05 187938     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7941000-b7942000 r--p 00006000 08:05 187938     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7942000-b7943000 rw-p 00007000 08:05 187938     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7943000-b7945000 rw-p b7943000 00:00 0 
b7945000-b7949000 r-xp 00000000 08:05 333513     /usr/lib/libXdmcp.so.6.0.0
b7949000-b794a000 rw-p 00003000 08:05 333513     /usr/lib/libXdmcp.so.6.0.0
b794a000-b794c000 r-xp 00000000 08:05 333511     /usr/lib/libXau.so.6.0.0
b794c000-b794d000 rw-p 00001000 08:05 333511     /usr/lib/libXau.so.6.0.0
b794d000-b794e000 rw-p b794d000 00:00 0 
b794e000-b7965000 r-xp 00000000 08:05 333536     /usr/lib/libxcb.so.1.0.0
b7965000-b7966000 r--p 00016000 08:05 333536     /usr/lib/libxcb.so.1.0.0
b7966000-b7967000 rw-p 00017000 08:05 333536     /usr/lib/libxcb.so.1.0.0
b7967000-b7968000 r-xp 00000000 08:05 333797     /usr/lib/libxcb-xlib.so.0.0.0
b7968000-b7969000 r--p 00000000 08:05 333797     /usr/lib/libxcb-xlib.so.0.0.0
b7969000-b796a000 rw-p 00001000 08:05 333797     /usr/lib/libxcb-xlib.so.0.0.0
b796a000-b7971000 r-xp 00000000 08:05 187947     /lib/tls/i686/cmov/librt-2.8.90.so
b7971000-b7972000 r--p 00007000 08:05 187947     /lib/tls/i686/cmov/librt-2.8.90.so
b7972000-b7973000 rw-p 00008000 08:05 187947     /lib/tls/i686/cmov/librt-2.8.90.so
b7973000-b797a000 r-xp 00000000 08:05 334101     /usr/lib/libdrm.so.2.3.1
b797a000-b797b000 r--p 00006000 08:05 334101     /usr/lib/libdrm.so.2.3.1
b797b000-b797c000 rw-p 00007000 08:05 334101     /usr/lib/libdrm.so.2.3.1
b797c000-b7980000 r-xp 00000000 08:05 334594     /usr/lib/libXfixes.so.3.1.0
b7980000-b7981000 rw-p 00003000 08:05 334594     /usr/lib/libXfixes.so.3.1.0
b7981000-b7982000 rw-p b7981000 00:00 0 
b7982000-b7984000 r-xp 00000000 08:05 335900     /usr/lib/libXdamage.so.1.1.0
b7984000-b7985000 rw-p 00001000 08:05 335900     /usr/lib/libXdamage.so.1.1.0
b7985000-b7989000 r-xp 00000000 08:05 333480     /usr/lib/libXxf86vm.so.1.0.0
b7989000-b798a000 r--p 00003000 08:05 333480     /usr/lib/libXxf86vm.so.1.0.0
b798a000-b798b000 rw-p 00004000 08:05 333480     /usr/lib/libXxf86vm.so.1.0.0
b798b000-b7998000 r-xp 00000000 08:05 334200     /usr/lib/libXext.so.6.4.0
b7998000-b799a000 rw-p 0000c000 08:05 334200     /usr/lib/libXext.so.6.4.0
b799a000-b7a85000 r-xp 00000000 08:05 333269     /usr/lib/libX11.so.6.2.0
b7a85000-b7a86000 r--p 000ea000 08:05 333269     /usr/lib/libX11.so.6.2.0
b7a86000-b7a88000 rw-p 000eb000 08:05 333269     /usr/lib/libX11.so.6.2.0
b7a88000-b7a89000 rw-p b7a88000 00:00 0 
b7a89000-b7a9c000 r-xp 00000000 08:05 336934     /usr/lib/libdirect-1.0.so.0.1.0
b7a9c000-b7a9d000 r--p 00012000 08:05 336934     /usr/lib/libdirect-1.0.so.0.1.0
b7a9d000-b7a9e000 rw-p 00013000 08:05 336934     /usr/lib/libdirect-1.0.so.0.1.0
b7a9e000-b7aa5000 r-xp 00000000 08:05 336936     /usr/lib/libfusion-1.0.so.0.1.0
b7aa5000-b7aa6000 r--p 00006000 08:05 336936     /usr/lib/libfusion-1.0.so.0.1.0
b7aa6000-b7aa7000 rw-p 00007000 08:05 336936     /usr/lib/libfusion-1.0.so.0.1.0
b7aa7000-b7aa8000 rw-p b7aa7000 00:00 0 
b7aa8000-b7b0c000 r-xp 00000000 08:05 336935     /usr/lib/libdirectfb-1.0.so.0.1.0
b7b0c000-b7b0d000 r--p 00063000 08:05 336935     /usr/lib/libdirectfb-1.0.so.0.1.0
b7b0d000-b7b0e000 rw-p 00064000 08:05 336935     /usr/lib/libdirectfb-1.0.so.0.1.0
b7b0e000-b7b10000 r-xp 00000000 08:05 187583     /lib/tls/i686/cmov/libdl-2.8.90.so
b7b10000-b7b11000 r--p 00001000 08:05 187583     /lib/tls/i686/cmov/libdl-2.8.90.so
b7b11000-b7b12000 rw-p 00002000 08:05 187583     /lib/tls/i686/cmov/libdl-2.8.90.so
b7b12000-b7bd5000 r-xp 00000000 08:05 333693     /usr/lib/libasound.so.2.0.0
b7bd5000-b7bd7000 r--p 000c2000 08:05 333693     /usr/lib/libasound.so.2.0.0
b7bd7000-b7bda000 rw-p 000c4000 08:05 333693     /usr/lib/libasound.so.2.0.0
b7bda000-b7bef000 r-xp 00000000 08:05 187945     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7bef000-b7bf0000 r--p 00014000 08:05 187945     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7bf0000-b7bf1000 rw-p 00015000 08:05 187945     /lib/tls/i686/cmov/libpthread-2.8.90.so
b7bf1000-b7bf3000 rw-p b7bf1000 00:00 0 
b7bf3000-b7d4b000 r-xp 00000000 08:05 187580     /lib/tls/i686/cmov/libc-2.8.90.so
b7d4b000-b7d4d000 r--p 00158000 08:05 187580     /lib/tls/i686/cmov/libc-2.8.90.so
b7d4d000-b7d4e000 rw-p 0015a000 08:05 187580     /lib/tls/i686/cmov/libc-2.8.90.so
b7d4e000-b7d52000 rw-p b7d4e000 00:00 0 
b7d52000-b7d5f000 r-xp 00000000 08:05 170967     /lib/libgcc_s.so.1
b7d5f000-b7d60000 r--p 0000c000 08:05 170967     /lib/libgcc_s.so.1
b7d60000-b7d61000 rw-p 0000d000 08:05 170967     /lib/libgcc_s.so.1
b7d61000-b7d85000 r-xp 00000000 08:05 187584     /lib/tls/i686/cmov/libm-2.8.90.so
b7d85000-b7d86000 r--p 00023000 08:05 187584     /lib/tls/i686/cmov/libm-2.8.90.so
b7d86000-b7d87000 rw-p 00024000 08:05 187584     /lib/tls/i686/cmov/libm-2.8.90.so
b7d87000-b7e6a000 r-xp 00000000 08:05 333605     /usr/lib/libstdc++.so.6.0.10
b7e6a000-b7e6b000 ---p 000e3000 08:05 333605     /usr/lib/libstdc++.so.6.0.10
b7e6b000-b7e6f000 r--p 000e3000 08:05 333605     /usr/lib/libstdc++.so.6.0.10
b7e6f000-b7e70000 rw-p 000e7000 08:05 333605     /usr/lib/libstdc++.so.6.0.10
b7e70000-b7e76000 rw-p b7e70000 00:00 0 
b7e76000-b7ecc000 r-xp 00000000 08:05 334005     /usr/lib/libGL.so.1.2
b7ecc000-b7ed1000 r--p 00055000 08:05 334005     /usr/lib/libGL.so.1.2
b7ed1000-b7ed6000 rwxp 0005a000 08:05 334005     /usr/lib/libGL.so.1.2
b7ed6000-b7ed7000 rwxp b7ed6000 00:00 0 
b7ed7000-b7eda000 r-xp 00000000 08:05 334633     /usr/lib/libao.so.2.1.3
b7eda000-b7edc000 rw-p 00003000 08:05 334633     /usr/lib/libao.so.2.1.3
b7edc000-b7f00000 r-xp 00000000 08:05 333762     /usr/lib/libpng12.so.0.27.0
b7f00000-b7f02000 rw-p 00023000 08:05 333762     /usr/lib/libpng12.so.0.27.0
b7f02000-b7f03000 rw-p b7f02000 00:00 0 
b7f03000-b7f6a000 r-xp 00000000 08:05 334762     /usr/lib/libSDL-1Aborted

```

Any ideas?

---

### Post by Vadi on 2008-10-27
I'm afraid I can't help with zsnes, but just a small correction, I think you meant "release candidate", not "release client" ;)

---

### Post by DoktorSeven on 2008-10-27
Yep, I get the same thing even after cleaning out ~/.zsnes.  Check the bug report [here](http://ubuntuforums.org/showthread.php?t=813785).

---

### Post by dfreer on 2008-10-28
Better yet, check out the thread on ZSNES forums:
[http://board.zsnes.com/phpBB2/viewtopic.php?t=12093&highlight=&sid=9f085631c05685fccb353502b389127b](http://board.zsnes.com/phpBB2/viewtopic.php?t=12093&highlight=&sid=9f085631c05685fccb353502b389127b)

Short answer: use a binary that wasn't compiled with Intrepid's GCC 4.3.2 release or compile yourself, once again not using GCC 4.3.2.

> **Vadi said:**
> I'm afraid I can't help with znes, but just a small correction, I think you meant "release candidate", not "release client" ;)

Just a small correction, I think you meant "zsnes", not "znes" ;)

---

### Post by Vadi on 2008-10-28
Thanks, fixed

---

### Post by 1337yit on 2008-10-29
Me being the slight noob I am, will this fix itself eventually through sudo apt-get upgrades?

---

### Post by DoktorSeven on 2008-10-29
> **1337yit said:**
> Me being the slight noob I am, will this fix itself eventually through sudo apt-get upgrades?

Possibly, but in the meantime there's a usable and working package linked on the page I linked to above ([here](http://ubuntuforums.org/showthread.php?t=813785)).

---

### Post by dfreer on 2008-10-29
> **DoktorSeven said:**
> Possibly, but in the meantime there's a usable and working package linked on the page I linked to above ([here](http://ubuntuforums.org/showthread.php?t=813785)).

Isn't that a link to the NES emulator, mednafen or am I reading it wrong? That won't help...

---

### Post by elustran on 2008-10-29
> **DoktorSeven said:**
> Possibly, but in the meantime there's a usable and working package linked on the page I linked to above ([here](http://ubuntuforums.org/showthread.php?t=813785)).
I'm confused - where's there a working package on that thread?  That looks like its for a totally different emulator.

---

### Post by dfreer on 2008-10-30
Will be updating my repository as soon as I work out a bug in the software, but for now you should be able to use the following attached binary (built in Debian Lenny). Note that since it's compiled with --enable-libao, you will need to have ia32-libs installed and renamed symbolic links from /usr/lib32/ao/plugins-2/* to /usr/lib/ao/plugins-2/.

You can also try the attached package as well, let me know if it works. It uses a binary built in Hardy, but the package is updated for Intrepid and contains symbolic links for those libao2 libaries:

EDIT: I have tested both binaries and they should be fine. It's the symbolic links in the intrepid package I'm most worried about, or some small error like a dependency spelled wrong.

---

### Post by FranMichaels on 2008-10-30
I can verify that i586 binary compiled by one of the zsnes devs works fine on Intrepid.

[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)

---

### Post by elustran on 2008-10-30
I got the binaries from [http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513) to work.  By default, it seems that they use X11 and bog down my system even though I've got an AMD X2 5000.  I had to configure it to run via GL in order to work.  Weird.  On my old Athalon xp, zsnes ran fine in X11 mode.  No sweat off my back, though, since I need GL output for fullscreening anyway.

The embarrassing part though, is that I now have no idea what to do with this binary that's sitting in a folder on my desktop.  How do I 'install' it?  I haven't had much luck finding a good tutorial.

Also, anybody know a good NES emulator?  I'm having problems with GFCE... crashed on controller input.  Going to try a few things and then probably start a new thread.

---

### Post by dfreer on 2008-10-30
> **elustran said:**
> The embarrassing part though, is that I now have no idea what to do with this binary that's sitting in a folder on my desktop.  How do I 'install' it?  I haven't had much luck finding a good tutorial.

"Installing" it is a matter of preference. Generally you'll want to place the binary somewhere in your path, that way when you use the terminal you can just type "zsnes" and it will launch regardless of what directory you are currently in. You can check out the directories in your path like so:
```
echo $PATH
```

When I create packages, I generally place all zsnes files in /usr/local/games/zsnes32/, and create a symbolic link from /usr/local/games/zsnes32/zsnes to /usr/bin/zsnes32.

Another idea is to create a folder called "bin" in your home directory and place it in there. Generally your ~/.bashrc should check for the presence of ~/bin/ and automatically add it to your path if it exists. You can also use this method when compiling zsnes, by giving it the following command when configuring:
```
./configure --prefix=$HOME
```

Adding it to your start menu is easy using "System > Preferences > Main Menu", just add a new launcher and point it to the binary. When creating packages, I create a .desktop file in /usr/local/applications/ and a icon in /usr/local/pixmaps/.

---

### Post by DoktorSeven on 2008-10-30
> **dfreer said:**
> Isn't that a link to the NES emulator, mednafen or am I reading it wrong? That won't help...

My fault.  I meant to have a link to a bug report in both places and somehow ended up pasting in the mednafen frontend link instead without checking.  That'll teach me to always check links after posting... 

Correct link is [here](https://bugs.launchpad.net/ubuntu/+source/zsnes/+bug/250425), a link to a bugs.launchpad.net bug report on zsnes.

---

### Post by ColeJayStooks on 2008-11-29
Thread seems a little older but I'm just going to try and install the Hardy deb from [here](http://packages.ubuntu.com/hardy/i386/zsnes/download) and see what happens. On Intrepid btw.

EDIT: So far so good...

EDIT2: Neato!

Seems to work just fine. Had to do that terminal trick to get zsnes to use sdl, but otherwise, everything was peaches.

Except now Update Manager is going to bug me all the time about updating it. :(

---

### Post by BigSilly on 2008-11-29
> **ColeJayStooks said:**
> Thread seems a little older but I'm just going to try and install the Hardy deb from [here](http://packages.ubuntu.com/hardy/i386/zsnes/download) and see what happens. On Intrepid btw.

EDIT: So far so good...

EDIT2: Neato!

Seems to work just fine. Had to do that terminal trick to get zsnes to use sdl, but otherwise, everything was peaches.

Except now Update Manager is going to bug me all the time about updating it. :(

Just lock the package in Synaptic. I've done that with the package I'm using (I think it's a Gutsy built one). It won't bother you then. Just open Synaptic and search for ZSNES, highlight the package you want, then click the "package" tab top left. Tick the box for Lock Version and job done.

Have fun!

---

### Post by ColeJayStooks on 2008-11-29
That's neat! Thanks man!

---

