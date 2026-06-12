---
title: "Mednafen 0.8.2-beta, adds support for GG and SMS!"
date: 2007-07-20
forum: Gaming &amp; Leisure
---

### Post by BoyOfDestiny on 2007-07-20
Just thought I'd mention Mednafen 0.8.2 beta adds support for Game Gear and Sega Master System.
Several fixes as well. Seems pretty sweet so far, with all the goodies you expect from Mednafen.

Tarball here.
[http://forum.fobby.net/index.php?t=msg&th=300&start=0&](http://forum.fobby.net/index.php?t=msg&th=300&start=0&)

Screenies below:

---

### Post by hikaricore on 2007-07-20
I feel old.  I remember owning a gameboy, and wanting to own a gamegear...

>.<

---

### Post by zazen666 on 2007-08-05
I downloaded the tarball, extracted it. When I try to run from the command line, I get an error that it is not intalled.

What do I do next, please

---

### Post by BoyOfDestiny on 2007-08-06
> **zazen666 said:**
> I downloaded the tarball, extracted it. When I try to run from the command line, I get an error that it is not intalled.

What do I do next, please

Hi, ok the tarball is just the source code. Now if you want to use mednafen for anything other than it's gg/sms support, use the one in the repos.

If you'd like to compile it, I'll try to make it easy (it is simple, after you've done it once ;) )

Ok new beta is out

[http://forum.fobby.net/index.php?t=msg&th=304&start=0&](http://forum.fobby.net/index.php?t=msg&th=304&start=0&)

after you download it

tar -xvf mednafen-0.8.3-beta.tar.bz2
cd mednafen

sudo apt-get install libcdio-dev libsdl1.2-dev libsdl-net1.2-dev libsndfile1-dev zlib1g-dev build-essential automake autoconf

Hopefully I didn't miss anything

./autogen.sh
./configure
make

sudo make install 

or if you'd like a deb
sudo apt-get install checkinstall
sudo checkinstall

---

### Post by zazen666 on 2007-08-09
HI-Thanks so much for the info, I wasnt able to try out what you said till today. 
I ran into some errors:
Could you look below, I quoted some of your instructions from above:

sudo apt-get install libcdio-dev libsdl1.2-dev libsdl-net1.2-dev libsndfile1-dev zlib1g-dev build-essential automake autoconf


This (above) step when fine.



./autogen.sh
./configure
make

sudo make install 

or if you'd like a deb
sudo apt-get install checkinstall
sudo checkinstall


These steps I had some errors.
 I pasted the terminal output below.
Could you advise me?

p
mednafen/src/ngp/TLCS-900h/TLCS900h_disassemble.h
mednafen/src/ngp/TLCS-900h/TLCS900h_disassemble_reg.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_disassemble_src.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret_dst.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret_reg.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret_dst.h
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret_reg.h
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret_single.h
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret_src.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapB.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeB0.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeB1.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeB2.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeB3.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeL0.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeL1.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeL2.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeL3.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeW0.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeW1.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeW2.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapCodeW3.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapL.h
mednafen/src/ngp/TLCS-900h/TLCS900h_registers_mapW.h
mednafen/src/ngp/TLCS-900h/TLCS900h_disassemble.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_disassemble_dst.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_disassemble_extra.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret_single.cpp
mednafen/src/ngp/TLCS-900h/TLCS900h_interpret_src.cpp
mednafen/src/ngp/Z80_interface.h
mednafen/src/ngp/gfx_scanline_colour.cpp
mednafen/src/ngp/rtc.cpp
mednafen/src/ngp/T6W28_Apu.h
mednafen/src/ngp/T6W28_Oscs.h
mednafen/src/ngp/T6W28_Apu.cpp
mednafen/src/ngp/rtc.h
mednafen/src/pce/
mednafen/src/pce/Makefile.am
mednafen/src/pce/hes.h
mednafen/src/pce/huc6280.cpp
mednafen/src/pce/huc.cpp
mednafen/src/pce/input.cpp
mednafen/src/pce/vdc.cpp
mednafen/src/pce/ops.h
mednafen/src/pce/vdc.h
mednafen/src/pce/pce.cpp
mednafen/src/pce/psg.cpp
mednafen/src/pce/psg-loop.h
mednafen/src/pce/pce.h
mednafen/src/pce/huc.h
mednafen/src/pce/huc6280.h
mednafen/src/pce/input.h
mednafen/src/pce/Makefile.in
mednafen/src/pce/hes.cpp
mednafen/src/pce/psg.h
mednafen/src/pce/adpcm.h
mednafen/src/pce/cdrom.cpp
mednafen/src/pce/adpcm.cpp
mednafen/src/pce/cdrom.h
mednafen/src/pce/debug.h
mednafen/src/pce/debug.cpp
mednafen/src/pce/tsushin.cpp
mednafen/src/pce/tsushin.h
mednafen/src/pcfx/
mednafen/src/pcfx/v810_cpu.cpp
mednafen/src/pcfx/v810_cpuD.cpp
mednafen/src/pcfx/v810_cpuD.h
mednafen/src/pcfx/v810_cpu.h
mednafen/src/pcfx/v810_opt.h
mednafen/src/pcfx/pcfx.cpp
mednafen/src/pcfx/pcfx.h
mednafen/src/pcfx/Makefile.in
mednafen/src/pcfx/interrupt.h
mednafen/src/pcfx/vdc.h
mednafen/src/pcfx/Makefile.am
mednafen/src/pcfx/soundbox.cpp
mednafen/src/pcfx/soundbox.h
mednafen/src/pcfx/psg-loop.h
mednafen/src/pcfx/input.h
mednafen/src/pcfx/king.cpp
mednafen/src/pcfx/vdc.cpp
mednafen/src/pcfx/king.h
mednafen/src/pcfx/timer.cpp
mednafen/src/pcfx/timer.h
mednafen/src/pcfx/debug.h
mednafen/src/pcfx/debug.cpp
mednafen/src/pcfx/fpu/
mednafen/src/pcfx/fpu/op-1.h
mednafen/src/pcfx/fpu/op-2.h
mednafen/src/pcfx/fpu/op-4.h
mednafen/src/pcfx/fpu/op-8.h
mednafen/src/pcfx/fpu/op-common.h
mednafen/src/pcfx/fpu/sfp-machine.h
mednafen/src/pcfx/fpu/single.h
mednafen/src/pcfx/fpu/soft-fp.h
mednafen/src/pcfx/rainbow.h
mednafen/src/pcfx/rainbow.cpp
mednafen/src/pcfx/jrevdct.h
mednafen/src/pcfx/jrevdct.cpp
mednafen/src/pcfx/interrupt.cpp
mednafen/src/pcfx/v810_eskimo.h
mednafen/src/pcfx/input.cpp
mednafen/src/pcfx/huc6273.cpp
mednafen/src/pcfx/huc6273.h
mednafen/src/player.cpp
mednafen/src/player.h
mednafen/src/psf.cpp
mednafen/src/psf.h
mednafen/src/quicklz.cpp
mednafen/src/quicklz.h
mednafen/src/scsicd.cpp
mednafen/src/scsicd.h
mednafen/src/selblur.cpp
mednafen/src/selblur.h
mednafen/src/settings-common.h
mednafen/src/settings.cpp
mednafen/src/settings-driver.h
mednafen/src/settings.h
mednafen/src/sexyal/
mednafen/src/sexyal/convert.h
mednafen/src/sexyal/sexyal.c
mednafen/src/sexyal/drivers/
mednafen/src/sexyal/drivers/sdl.c
mednafen/src/sexyal/drivers/osxcoreaudio.c
mednafen/src/sexyal/drivers/jack.c
mednafen/src/sexyal/drivers/oss.h
mednafen/src/sexyal/drivers/dsound.c
mednafen/src/sexyal/drivers/oss.c
mednafen/src/sexyal/drivers/alsa.c
mednafen/src/sexyal/drivers/alsa.h
mednafen/src/sexyal/sexyal.h
mednafen/src/sexyal/smallc.c
mednafen/src/sexyal/smallc.h
mednafen/src/sexyal/Makefile.am.inc
mednafen/src/sexyal/convert.c
mednafen/src/sexyal/COPYING
mednafen/src/sexyal/README
mednafen/src/sms/
mednafen/src/sms/pio.cpp
mednafen/src/sms/sms.cpp
mednafen/src/sms/shared.h
mednafen/src/sms/vdp.h
mednafen/src/sms/system.h
mednafen/src/sms/vdp.cpp
mednafen/src/sms/cpu/
mednafen/src/sms/cpu/z80.c
mednafen/src/sms/cpu/z80.h
mednafen/src/sms/cpu/z80daa.h
mednafen/src/sms/cpu/osd_cpu.h
mednafen/src/sms/cpu/cpuintrf.h
mednafen/src/sms/cpu/memory.h
mednafen/src/sms/render.h
mednafen/src/sms/romdb.h
mednafen/src/sms/sms.h
mednafen/src/sms/hvc.h
mednafen/src/sms/system.cpp
mednafen/src/sms/state.h
mednafen/src/sms/romdb.cpp
mednafen/src/sms/memz80.cpp
mednafen/src/sms/Makefile.in
mednafen/src/sms/Makefile.am
mednafen/src/sms/emu2413.h
mednafen/src/sms/pio.h
mednafen/src/sms/memz80.h
mednafen/src/sms/docs/
mednafen/src/sms/docs/readme.txt
mednafen/src/sms/docs/porting.txt
mednafen/src/sms/docs/compatability.txt
mednafen/src/sms/docs/license
mednafen/src/sms/docs/changelog
mednafen/src/sms/sound.cpp
mednafen/src/sms/sound.h
mednafen/src/sms/2413tone.h
mednafen/src/sms/Sms_Apu.cpp
mednafen/src/sms/Sms_Apu.h
mednafen/src/sms/Sms_Oscs.h
mednafen/src/sms/cart.cpp
mednafen/src/sms/tms.h
mednafen/src/sms/tms.cpp
mednafen/src/sms/render.cpp
mednafen/src/sms/cart.h
mednafen/src/sms/emu2413.cpp
mednafen/src/state.cpp
mednafen/src/state-driver.h
mednafen/src/state.h
mednafen/src/Stereo_Buffer.cpp
mednafen/src/tests.cpp
mednafen/src/tests.h
mednafen/src/tremor/
mednafen/src/tremor/Makefile.in
mednafen/src/tremor/asm_arm.h
mednafen/src/tremor/autogen.sh
mednafen/src/tremor/backends.h
mednafen/src/tremor/bitwise.c
mednafen/src/tremor/block.c
mednafen/src/tremor/block.h
mednafen/src/tremor/CHANGELOG
mednafen/src/tremor/codebook.c
mednafen/src/tremor/codebook.h
mednafen/src/tremor/codec_internal.h
mednafen/src/tremor/config_types.h
mednafen/src/tremor/COPYING
mednafen/src/tremor/floor0.c
mednafen/src/tremor/floor1.c
mednafen/src/tremor/framing.c
mednafen/src/tremor/info.c
mednafen/src/tremor/ivorbiscodec.h
mednafen/src/tremor/ivorbisfile.h
mednafen/src/tremor/lsp_lookup.h
mednafen/src/tremor/Makefile.am
mednafen/src/tremor/mapping0.c
mednafen/src/tremor/mdct.c
mednafen/src/tremor/mdct.h
mednafen/src/tremor/mdct_lookup.h
mednafen/src/tremor/misc.h
mednafen/src/tremor/ogg.h
mednafen/src/tremor/os.h
mednafen/src/tremor/os_types.h
mednafen/src/tremor/README
mednafen/src/tremor/registry.c
mednafen/src/tremor/registry.h
mednafen/src/tremor/res012.c
mednafen/src/tremor/sharedbook.c
mednafen/src/tremor/synthesis.c
mednafen/src/tremor/vorbisfile.c
mednafen/src/tremor/window.c
mednafen/src/tremor/window.h
mednafen/src/tremor/window_lookup.h
mednafen/src/trio/
mednafen/src/trio/trio.c
mednafen/src/trio/trionan.c
mednafen/src/trio/triostr.c
mednafen/src/trio/Makefile.in
mednafen/src/trio/.dirstamp
mednafen/src/trio/Makefile.am
mednafen/src/types.h
mednafen/src/unzip.c
mednafen/src/unzip.h
mednafen/src/video/
mednafen/src/video/font18x18.h
mednafen/src/video/font5x7.h
mednafen/src/video/font9x18.h
mednafen/src/video/video.cpp
mednafen/src/video/text.cpp
mednafen/src/video/png.cpp
mednafen/src/video/primitives.cpp
mednafen/src/video/video-common.h
mednafen/src/video/Makefile.am.inc
mednafen/src/video/font-data.cpp
mednafen/src/video/font-data.h
mednafen/src/video/font-data-18x18.c
mednafen/src/video/primitives.h
mednafen/src/video/text.h
mednafen/src/video/font6x13.h
mednafen/src/video/font12x13.h
mednafen/src/video/font-data-12x13.c
mednafen/src/video/font4x5.h
mednafen/src/video-driver.h
mednafen/src/video.h
mednafen/src/wave.cpp
mednafen/src/wave.h
mednafen/src/world_strtod.c
mednafen/src/world_strtod.h
mednafen/src/wswan/
mednafen/src/wswan/eeprom.h
mednafen/src/wswan/gfx.cpp
mednafen/src/wswan/gfx.h
mednafen/src/wswan/main.cpp
mednafen/src/wswan/memory.cpp
mednafen/src/wswan/memory.h
mednafen/src/wswan/Makefile.in
mednafen/src/wswan/start.h
mednafen/src/wswan/tcache.cpp
mednafen/src/wswan/v30mz.h
mednafen/src/wswan/Makefile.am
mednafen/src/wswan/sound.cpp
mednafen/src/wswan/wswan.h
mednafen/src/wswan/sound.h
mednafen/src/wswan/dis/
mednafen/src/wswan/dis/disasm.h
mednafen/src/wswan/dis/dis_groups.cpp
mednafen/src/wswan/dis/resolve.cpp
mednafen/src/wswan/dis/dis_tables.h
mednafen/src/wswan/dis/dis_tables.inc
mednafen/src/wswan/dis/opcodes.inc
mednafen/src/wswan/dis/syntax.cpp
mednafen/src/wswan/dis/dis_decode.cpp
mednafen/src/wswan/wstech24.txt
mednafen/src/wswan/v30mz.cpp
mednafen/src/wswan/eeprom.cpp
mednafen/src/wswan/interrupt.h
mednafen/src/wswan/interrupt.cpp
mednafen/src/wswan/debug.h
mednafen/src/wswan/rtc.cpp
mednafen/src/wswan/rtc.h
mednafen/src/wswan/v30mz-private.h
mednafen/src/wswan/v30mz-ea.h
mednafen/src/wswan/v30mz-modrm.h
mednafen/src/wswan/debug.cpp
mednafen/src/Ym2612_Emu.cpp
mednafen/src/Ym2612_Emu.h
mednafen/config.guess
mednafen/acinclude.m4
mednafen/mkinstalldirs
mednafen/COPYING
mednafen/compile
mednafen/m4/
mednafen/m4/codeset.m4
mednafen/m4/gettext.m4
mednafen/m4/glibc2.m4
mednafen/m4/glibc21.m4
mednafen/m4/iconv.m4
mednafen/m4/intdiv0.m4
mednafen/m4/intmax.m4
mednafen/m4/inttypes_h.m4
mednafen/m4/inttypes-h.m4
mednafen/m4/inttypes-pri.m4
mednafen/m4/lcmessage.m4
mednafen/m4/lib-ld.m4
mednafen/m4/lib-link.m4
mednafen/m4/lib-prefix.m4
mednafen/m4/lock.m4
mednafen/m4/longdouble.m4
mednafen/m4/longlong.m4
mednafen/m4/nls.m4
mednafen/m4/po.m4
mednafen/m4/printf-posix.m4
mednafen/m4/progtest.m4
mednafen/m4/signed.m4
mednafen/m4/size_max.m4
mednafen/m4/stdint_h.m4
mednafen/m4/uintmax_t.m4
mednafen/m4/ulonglong.m4
mednafen/m4/visibility.m4
mednafen/m4/wchar_t.m4
mednafen/m4/wint_t.m4
mednafen/m4/xsize.m4
mednafen/m4/ChangeLog
mednafen/config.status.lineno
marshal@marshal-laptop:~$ cd mednafen
marshal@marshal-laptop:~/mednafen$ sudo apt-get install libcdio-dev libsdl1.2-dev libsdl-net1.2-dev libsndfile1-dev zlib1g-dev build-essential automake autoconf
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
zlib1g-dev is already the newest version.
zlib1g-dev set to manual installed.
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  python-pygame libcairomm-1.0-1
  libglibmm-2.4-1c2a libsdl-ttf2.0-0
  kdebase-bin libgtkmm-2.4-1c2a
  libsdl-mixer1.2 libassa3.4-0 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autotools-dev libflac-dev libgl1-mesa-dev
  libglu1-mesa-dev libglu1-xorg-dev
  mesa-common-dev
Suggested packages:
  autoconf2.13 autobook autoconf-archive
  gnu-standards autoconf-doc automake1.10-doc
Recommended packages:
  automaken libxt-dev libasound2-dev
  libaa1-dev libaudio-dev libartsc0-dev
  libesd0-dev libdirectfb-dev libcaca-dev
  libcucul-dev
The following NEW packages will be installed:
  autoconf automake autotools-dev libcdio-dev
  libflac-dev libgl1-mesa-dev libglu1-mesa-dev
  libglu1-xorg-dev libsdl-net1.2-dev
  libsdl1.2-dev libsndfile1-dev
  mesa-common-dev
0 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 2943kB of archives.
After unpacking 11.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main autoconf 2.61-3 [448kB]
Get:2 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main autotools-dev 20060920.1 [61.1kB]
Get:3 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main automake 1:1.10+nogfdl-1 [369kB]
Get:4 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main libcdio-dev 0.76-1ubuntu2 [219kB]
Get:5 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main libflac-dev 1.1.2-5ubuntu2 [196kB]
Get:6 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main mesa-common-dev 6.5.2-3ubuntu8 [175kB]
Get:7 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main libgl1-mesa-dev 6.5.2-3ubuntu8 [25.0kB]
Get:8 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty-updates/main libglu1-mesa-dev 6.5.2-3ubuntu8 [257kB]
Get:9 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main libglu1-xorg-dev 1:7.2-0ubuntu11 [25.6kB]
Get:10 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main libsdl1.2-dev 1.2.11-7ubuntu1 [839kB]
Get:11 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/universe libsdl-net1.2-dev 1.2.5-7 [15.8kB]
Get:12 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) feisty/main libsndfile1-dev 1.0.16-1build1 [314kB]
Fetched 2943kB in 7s (399kB/s)                 
Selecting previously deselected package autoconf.
(Reading database ... 112543 files and directories currently installed.)
Unpacking autoconf (from .../autoconf_2.61-3_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20060920.1_all.deb) ...
Selecting previously deselected package automake.
Unpacking automake (from .../automake_1%3a1.10+nogfdl-1_all.deb) ...
Selecting previously deselected package libcdio-dev.
Unpacking libcdio-dev (from .../libcdio-dev_0.76-1ubuntu2_i386.deb) ...
Selecting previously deselected package libflac-dev.
Unpacking libflac-dev (from .../libflac-dev_1.1.2-5ubuntu2_i386.deb) ...
Selecting previously deselected package mesa-common-dev.
Unpacking mesa-common-dev (from .../mesa-common-dev_6.5.2-3ubuntu8_all.deb) ...
Selecting previously deselected package libgl1-mesa-dev.
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_6.5.2-3ubuntu8_all.deb) ...
Selecting previously deselected package libglu1-mesa-dev.
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_6.5.2-3ubuntu8_i386.deb) ...
Selecting previously deselected package libglu1-xorg-dev.
Unpacking libglu1-xorg-dev (from .../libglu1-xorg-dev_1%3a7.2-0ubuntu11_all.deb) ...
Selecting previously deselected package libsdl1.2-dev.
Unpacking libsdl1.2-dev (from .../libsdl1.2-dev_1.2.11-7ubuntu1_i386.deb) ...
Selecting previously deselected package libsdl-net1.2-dev.
Unpacking libsdl-net1.2-dev (from .../libsdl-net1.2-dev_1.2.5-7_i386.deb) ...
Selecting previously deselected package libsndfile1-dev.
Unpacking libsndfile1-dev (from .../libsndfile1-dev_1.0.16-1build1_i386.deb) ...
Setting up autoconf (2.61-3) ...

Setting up autotools-dev (20060920.1) ...
Setting up automake (1.10+nogfdl-1) ...

Setting up libcdio-dev (0.76-1ubuntu2) ...
Setting up libflac-dev (1.1.2-5ubuntu2) ...
Setting up mesa-common-dev (6.5.2-3ubuntu8) ...
Setting up libgl1-mesa-dev (6.5.2-3ubuntu8) ...
Setting up libglu1-mesa-dev (6.5.2-3ubuntu8) ...
Setting up libglu1-xorg-dev (7.2-0ubuntu11) ...
Setting up libsdl1.2-dev (1.2.11-7ubuntu1) ...

Setting up libsdl-net1.2-dev (1.2.5-7) ...
Setting up libsndfile1-dev (1.0.16-1build1) ...

marshal@marshal-laptop:~/mednafen$ ./autogen.sh
./autogen.sh: 3: libtoolize: not found
configure.ac:19: warning: macro `AM_PROG_LIBTOOL' not found in library
configure.ac:58: warning: macro `AM_ICONV' not found in library
configure.ac:59: warning: macro `AM_GNU_GETTEXT' not found in library
configure.ac:19: error: possibly undefined macro: AM_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:58: error: possibly undefined macro: AM_ICONV
configure.ac:59: error: possibly undefined macro: AM_GNU_GETTEXT
src/gb/Makefile.am:5: library used but `RANLIB' is undefined
src/gb/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/gb/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/gba/Makefile.am:5: library used but `RANLIB' is undefined
src/gba/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/gba/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/lynx/Makefile.am:5: library used but `RANLIB' is undefined
src/lynx/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/lynx/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/mpcdec/Makefile.am:3: library used but `RANLIB' is undefined
src/mpcdec/Makefile.am:3:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/mpcdec/Makefile.am:3:   to `configure.ac' and run `autoconf' again.
src/nes/Makefile.am:5: library used but `RANLIB' is undefined
src/nes/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/nes/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/ngp/Makefile.am:5: library used but `RANLIB' is undefined
src/ngp/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/ngp/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/pce/Makefile.am:5: library used but `RANLIB' is undefined
src/pce/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/pce/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/pcfx/Makefile.am:5: library used but `RANLIB' is undefined
src/pcfx/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/pcfx/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/sms/Makefile.am:5: library used but `RANLIB' is undefined
src/sms/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/sms/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/tremor/Makefile.am:3: library used but `RANLIB' is undefined
src/tremor/Makefile.am:3:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/tremor/Makefile.am:3:   to `configure.ac' and run `autoconf' again.
src/trio/Makefile.am:5: library used but `RANLIB' is undefined
src/trio/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/trio/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/wswan/Makefile.am:5: library used but `RANLIB' is undefined
src/wswan/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/wswan/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
marshal@marshal-laptop:~/mednafen$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
./configure: line 4754: AM_PROG_LIBTOOL: command not found
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for ptrdiff_t... yes
checking for size_t... yes
checking for short... yes
checking size of short... 2
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for long long... yes
checking size of long long... 8
checking for double... yes
checking size of double... 8
checking for __int64... no
checking size of __int64... 0
checking for void *... yes
checking size of void *... 4
checking for size_t... (cached) yes
checking size of size_t... 4
checking for ptrdiff_t... (cached) yes
checking size of ptrdiff_t... 4
checking for an ANSI C-conforming const... yes
checking for memcmp... yes
checking for memcpy... yes
checking for memmove... yes
checking for memset... yes
checking for signal... yes
checking for fcntl... yes
checking for getenv... yes
checking for putenv... yes
checking for setenv... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for mkdir... yes
checking for _mkdir... no
checking whether mkdir takes one argument... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking OpenGL/gl.h usability... no
checking OpenGL/gl.h presence... no
checking for OpenGL/gl.h... no
checking for X... libraries , headers 
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
./configure: line 10169: AM_ICONV: command not found
./configure: line 10170: AM_GNU_GETTEXT: command not found
checking for zlibVersion in -lz... yes
checking OPTIMIZER_FLAGS for gcc -fomit-frame-pointer... -fomit-frame-pointer
checking OPTIMIZER_FLAGS for gcc -finline-limit=6000... -finline-limit=6000
checking OPTIMIZER_FLAGS for gcc --param large-function-growth=800... --param large-function-growth=800
checking OPTIMIZER_FLAGS for gcc --param inline-unit-growth=175... --param inline-unit-growth=175
checking OPTIMIZER_FLAGS for gcc --param max-inline-insns-single=10000... --param max-inline-insns-single=10000
checking OPTIMIZER_FLAGS for gcc -fno-strict-overflow... no, unknown
checking WARNING_FLAGS for gcc -Wall... -Wall
checking WARNING_FLAGS for gcc -Winline... -Winline
checking WARNING_FLAGS for gcc -Wshadow... -Wshadow
checking GBA_EXTRA_FLAGS for gcc -fno-unit-at-a-time... -fno-unit-at-a-time
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.0... not present.
checking for snd_ctl_open in -lasound... no
checking for JACK... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for LIBCDIO... yes
checking for SNDFILE... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking SDL_net.h usability... yes
checking SDL_net.h presence... yes
checking for SDL_net.h... yes
checking whether byte ordering is bigendian... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/tremor/Makefile
config.status: creating src/mpcdec/Makefile
config.status: creating src/trio/Makefile
config.status: creating src/gb/Makefile
config.status: creating src/gba/Makefile
config.status: creating src/lynx/Makefile
config.status: creating src/pce/Makefile
config.status: creating src/pcfx/Makefile
config.status: creating src/sms/Makefile
config.status: creating src/wswan/Makefile
config.status: creating src/nes/Makefile
config.status: creating src/ngp/Makefile
config.status: creating po/Makefile.in
config.status: creating intl/Makefile
config.status: creating include/config.h
config.status: executing depfiles commands
marshal@marshal-laptop:~/mednafen$ make
 cd . && /bin/bash /home/marshal/mednafen/missing --run automake-1.10 --gnu 
src/gb/Makefile.am:5: library used but `RANLIB' is undefined
src/gb/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/gb/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/gba/Makefile.am:5: library used but `RANLIB' is undefined
src/gba/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/gba/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/lynx/Makefile.am:5: library used but `RANLIB' is undefined
src/lynx/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/lynx/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/mpcdec/Makefile.am:3: library used but `RANLIB' is undefined
src/mpcdec/Makefile.am:3:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/mpcdec/Makefile.am:3:   to `configure.ac' and run `autoconf' again.
src/nes/Makefile.am:5: library used but `RANLIB' is undefined
src/nes/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/nes/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/ngp/Makefile.am:5: library used but `RANLIB' is undefined
src/ngp/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/ngp/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/pce/Makefile.am:5: library used but `RANLIB' is undefined
src/pce/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/pce/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/pcfx/Makefile.am:5: library used but `RANLIB' is undefined
src/pcfx/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/pcfx/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/sms/Makefile.am:5: library used but `RANLIB' is undefined
src/sms/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/sms/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/tremor/Makefile.am:3: library used but `RANLIB' is undefined
src/tremor/Makefile.am:3:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/tremor/Makefile.am:3:   to `configure.ac' and run `autoconf' again.
src/trio/Makefile.am:5: library used but `RANLIB' is undefined
src/trio/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/trio/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/wswan/Makefile.am:5: library used but `RANLIB' is undefined
src/wswan/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/wswan/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
make: *** [Makefile.in] Error 1
marshal@marshal-laptop:~/mednafen$ sudo apt-get install checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
checkinstall is already the newest version.
The following packages were automatically installed and are no longer required:
  python-pygame libcairomm-1.0-1
  libglibmm-2.4-1c2a libsdl-ttf2.0-0
  kdebase-bin libgtkmm-2.4-1c2a
  libsdl-mixer1.2 libassa3.4-0 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
marshal@marshal-laptop:~/mednafen$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> mednafen test
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@marshal-laptop ]
1 -  Summary: [ mednafen test ]
2 -  Name:    [ mednafen ]
3 -  Version: [ 0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3
0.8.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ mednafen ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
 cd . && /bin/bash /home/marshal/mednafen/missing --run automake-1.10 --gnu 
src/gb/Makefile.am:5: library used but `RANLIB' is undefined
src/gb/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/gb/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/gba/Makefile.am:5: library used but `RANLIB' is undefined
src/gba/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/gba/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/lynx/Makefile.am:5: library used but `RANLIB' is undefined
src/lynx/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/lynx/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/mpcdec/Makefile.am:3: library used but `RANLIB' is undefined
src/mpcdec/Makefile.am:3:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/mpcdec/Makefile.am:3:   to `configure.ac' and run `autoconf' again.
src/nes/Makefile.am:5: library used but `RANLIB' is undefined
src/nes/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/nes/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/ngp/Makefile.am:5: library used but `RANLIB' is undefined
src/ngp/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/ngp/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/pce/Makefile.am:5: library used but `RANLIB' is undefined
src/pce/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/pce/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/pcfx/Makefile.am:5: library used but `RANLIB' is undefined
src/pcfx/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/pcfx/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/sms/Makefile.am:5: library used but `RANLIB' is undefined
src/sms/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/sms/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/tremor/Makefile.am:3: library used but `RANLIB' is undefined
src/tremor/Makefile.am:3:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/tremor/Makefile.am:3:   to `configure.ac' and run `autoconf' again.
src/trio/Makefile.am:5: library used but `RANLIB' is undefined
src/trio/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/trio/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
src/wswan/Makefile.am:5: library used but `RANLIB' is undefined
src/wswan/Makefile.am:5:   The usual way to define `RANLIB' is to add `AC_PROG_RANLIB'
src/wswan/Makefile.am:5:   to `configure.ac' and run `autoconf' again.
make: *** [Makefile.in] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by hikaricore on 2007-08-09
Good god, you didn't have to post the whole thing lol.

Have you tried:

```
sudo make install
```

Instead of checkinstall?

---

### Post by BoyOfDestiny on 2007-08-09
> **zazen666 said:**
> HI-Thanks so much for the info, I wasnt able to try out what you said till today. 
I ran into some errors:
Could you look below, I quoted some of your instructions from above:

marshal@marshal-laptop:~/mednafen$ ./autogen.sh
./autogen.sh: 3: libtoolize: not found

make: *** [Makefile.in] Error 1


Very close.

I just clipped that message out showing that message. Just install libtool.

sudo apt-get install libtool gettext

(I think gettext is needed too, for multiple localization support)

If you see any "missing" stuff try searching for it in synaptic (so I guess I forgot something. Trust me though, once you have the dependencies installed, you don't have to do it again.) Sometimes missing stuff is like nameofit-dev, etc. 

so do so and retry with 
./autogen.sh
./configure
make clean
make

make clean starts it from scratch. Not necessary I think, but just incase I do it sometimes if I've installed new stuff.

Now if you see this error again:

> **zazen666 said:**
> 
make: *** [Makefile.in] Error 1


something is still amiss. So double check for something "missing"
If you have no errors, then do sudo checkinstall or sudo make install

Good luck!

EDIT try this first!: Actually since mednafen is in the repos, and should have the same build dependencies as the beta, try this
from the mednafen directory
sudo apt-get build-dep mednafen
./autogen.sh && ./configure && make clean && make
sudo checkinstall

I'm thinking that'll do it no problem. :)

---

### Post by zazen666 on 2007-08-09
[QUOTE
EDIT try this first!: Actually since mednafen is in the repos, and should have the same build dependencies as the beta, try this
from the mednafen directory
sudo apt-get build-dep mednafen
./autogen.sh && ./configure && make clean && make
sudo checkinstall

I'm thinking that'll do it no problem. :)[/QUOTE]

Hey man thanks for getting back to me:
Ok, so I am a bit lost at this point. I assume that I should now do the following, in the following order:
One Install mednafen from the repos
Two cd to the mednafen directory
Three  sudo apt-get build-dep mednafen
wait until that finishes, then
Four  ./autogen.sh && ./configure && make clean && make
Wait till that finishes, then,
Five sudo checkinstall

and that should do it?
Thanks SO much for helping, this is a new thing for me.
Also, sorry I posted so much, but literally, i ddn't know what was necessary and was not necessary info...
cheers

---

### Post by BoyOfDestiny on 2007-08-09
> **zazen666 said:**
> 
Hey man thanks for getting back to me:
Ok, so I am a bit lost at this point. I assume that I should now do the following, in the following order:
One Install mednafen from the repos
Two cd to the mednafen directory
Three  sudo apt-get build-dep mednafen
wait until that finishes, then
Four  ./autogen.sh && ./configure && make clean && make
Wait till that finishes, then,
Five sudo checkinstall

and that should do it?
Thanks SO much for helping, this is a new thing for me.
Also, sorry I posted so much, but literally, i ddn't know what was necessary and was not necessary info...
cheers

All good. You don't have to install the repo version.
The build-dep with apt just gets the files you need to build the package (which should be the same for the new version too)

so just start from step 2, and see how it goes.

It's a good learning experience for sure. I'm very glad to help.

---

### Post by zazen666 on 2007-08-09
okay, so I am on step three, and Iget this error:

 mv -f $depbase.Tpo $depbase.Po
../dis6280.h:2: warning: ‘class Dis6280’ has virtual functions but non-virtual destructor
debug.cpp:193: warning: ‘class DisPCE’ has virtual functions but non-virtual destructor
debug.cpp: In function ‘char* PCEDBG_ShiftJIS_to_UTF8(uint16)’:
debug.cpp:493: error: ‘ICONV_CONST’ was not declared in this scope
debug.cpp:493: error: expected `)' before ‘char’
make[2]: *** [debug.o] Error 1
make[2]: Leaving directory `/home/marshal/mednafen/src/pce'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/marshal/mednafen/src'
make: *** [all-recursive] Error 1

How can I tell what i need to sudo apt-get install?

thanks

---

### Post by BoyOfDestiny on 2007-08-09
> **zazen666 said:**
> okay, so I am on step three, and Iget this error:

 mv -f $depbase.Tpo $depbase.Po
../dis6280.h:2: warning: ‘class Dis6280’ has virtual functions but non-virtual destructor
debug.cpp:193: warning: ‘class DisPCE’ has virtual functions but non-virtual destructor
debug.cpp: In function ‘char* PCEDBG_ShiftJIS_to_UTF8(uint16)’:
debug.cpp:493: error: ‘ICONV_CONST’ was not declared in this scope
debug.cpp:493: error: expected `)' before ‘char’
make[2]: *** [debug.o] Error 1
make[2]: Leaving directory `/home/marshal/mednafen/src/pce'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/marshal/mednafen/src'
make: *** [all-recursive] Error 1

How can I tell what i need to sudo apt-get install?

thanks

hmm can't tell from that... Are there any errors or complaints of things missing during ./autogen.sh or ./configure?

maybe try a 
make clean
then 
make

---

### Post by zazen666 on 2007-08-09
Hey I finally got it working!!!!
I downloaded the latest version here (which is like 8.4):

[https://sourceforge.net/project/showfiles.php?group_id=150840&package_id=166686](https://sourceforge.net/project/showfiles.php?group_id=150840&package_id=166686)


and did the following:



tar -jxvf mednafen-0.8.4-rc1.tar.bz2
cd mednafen
./configure
sudo make
sudo make install


When I just did 
make
make install

I was getting permision errors



I was also told that prior to the above steps I might need to:

sudo apt-get install libcdio-dev libsdl1.2-dev libsdl-net1.2-dev libsdl-net1.2-dev zlib1g-dev gcc g++ make cpp binutils


but i did not

thanks for all your help

---

### Post by BoyOfDestiny on 2007-08-09
> **zazen666 said:**
> Hey I finally got it working!!!!
I downloaded the latest version here (which is like 8.4):

[https://sourceforge.net/project/showfiles.php?group_id=150840&package_id=166686](https://sourceforge.net/project/showfiles.php?group_id=150840&package_id=166686)


and did the following:



tar -jxvf mednafen-0.8.4-rc1.tar.bz2
cd mednafen
./configure
sudo make
sudo make install


When I just did 
make
make install

I was getting permision errors



I was also told that prior to the above steps I might need to:

sudo apt-get install libcdio-dev libsdl1.2-dev libsdl-net1.2-dev libsdl-net1.2-dev zlib1g-dev gcc g++ make cpp binutils


but i did not

thanks for all your help

Very cool! 

Thanks for mentioning the release, I didn't know the rc1 was out yet.

---

### Post by zazen666 on 2007-08-09
thanks for all your help by the way.....

---

### Post by zazen666 on 2007-08-09
any idea how to do full screen?

i tried adding 

-fs

but that does not seem to work?

---

### Post by BoyOfDestiny on 2007-08-09
> **zazen666 said:**
> any idea how to do full screen?

i tried adding 

-fs

but that does not seem to work?

Glad to have been able to help.

for fullscreen

alt + enter

Press F1 in mednafen to get some of the common key shortcuts.

---

