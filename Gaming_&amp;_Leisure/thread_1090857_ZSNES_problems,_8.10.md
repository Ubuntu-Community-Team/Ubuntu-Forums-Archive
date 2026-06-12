---
title: "ZSNES problems, 8.10"
date: 2009-03-08
forum: Gaming &amp; Leisure
---

### Post by BaineVII on 2009-03-08
A friend of mine wanted to use the Networking option on the ZSNES, and so I was attempting to install a different version than the one on the add/remove list...after failing miserably I tried to run the one I already had, and it doesn't seem to work anymore. I've tried removing the ap and re-adding it, but it still doesn't work. I'd really appreciate help. The error message is as follows:

```

ZSNES v1.36 (c) 1997-2002, ZSNES Team (zsKnight & _Demo_)

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before using it.

Use ZSNES -? for command line definitions.

*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7e01558]
/lib/tls/i686/cmov/libc.so.6[0xb7dff680]
/lib/tls/i686/cmov/libc.so.6(__strcpy_chk+0x44)[0xb7dfe944]
zsnes[0x81259ef]
zsnes[0x8049d41]
======= Memory map: ========
08048000-08124000 rwxp 00000000 08:06 4597978    /usr/local/bin/zsnes
08124000-08125000 r-xp 000dc000 08:06 4597978    /usr/local/bin/zsnes
08125000-082b4000 rwxp 000dd000 08:06 4597978    /usr/local/bin/zsnes
082b4000-082de000 rwxp 0026b000 08:06 4597978    /usr/local/bin/zsnes
082de000-0850e000 rwxp 082de000 00:00 0 
09c26000-09c47000 rwxp 09c26000 00:00 0          [heap]
b7cdc000-b7cdd000 rwxp b7cdc000 00:00 0 
b7cdd000-b7cdf000 r-xp 00000000 08:06 3196059    /lib/tls/i686/cmov/libdl-2.8.90.so
b7cdf000-b7ce0000 r-xp 00001000 08:06 3196059    /lib/tls/i686/cmov/libdl-2.8.90.so
b7ce0000-b7ce1000 rwxp 00002000 08:06 3196059    /lib/tls/i686/cmov/libdl-2.8.90.so
b7ce1000-b7d05000 r-xp 00000000 08:06 3196061    /lib/tls/i686/cmov/libm-2.8.90.so
b7d05000-b7d06000 r-xp 00023000 08:06 3196061    /lib/tls/i686/cmov/libm-2.8.90.so
b7d06000-b7d07000 rwxp 00024000 08:06 3196061    /lib/tls/i686/cmov/libm-2.8.90.so
b7d07000-b7e5f000 r-xp 00000000 08:06 3196053    /lib/tls/i686/cmov/libc-2.8.90.so
b7e5f000-b7e61000 r-xp 00158000 08:06 3196053    /lib/tls/i686/cmov/libc-2.8.90.so
b7e61000-b7e62000 rwxp 0015a000 08:06 3196053    /lib/tls/i686/cmov/libc-2.8.90.so
b7e62000-b7e66000 rwxp b7e62000 00:00 0 
b7e66000-b7e7b000 r-xp 00000000 08:06 3196079    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7e7b000-b7e7c000 r-xp 00014000 08:06 3196079    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7e7c000-b7e7d000 rwxp 00015000 08:06 3196079    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7e7d000-b7e7f000 rwxp b7e7d000 00:00 0 
b7e7f000-b7e8c000 r-xp 00000000 08:06 3178558    /lib/libgcc_s.so.1
b7e8c000-b7e8d000 r-xp 0000c000 08:06 3178558    /lib/libgcc_s.so.1
b7e8d000-b7e8e000 rwxp 0000d000 08:06 3178558    /lib/libgcc_s.so.1
b7e8e000-b7e8f000 rwxp b7e8e000 00:00 0 
b7e8f000-b7ed9000 r-xp 00000000 08:06 4597759    /usr/local/lib/libSDL-1.2.so.0.11.2
b7ed9000-b7eda000 r-xp 00049000 08:06 4597759    /usr/local/lib/libSDL-1.2.so.0.11.2
b7eda000-b7edb000 rwxp 0004a000 08:06 4597759    /usr/local/lib/libSDL-1.2.so.0.11.2
b7edb000-b7f04000 rwxp b7edb000 00:00 0 
b7f04000-b7f1e000 r-xp 00000000 08:06 3178515    /lib/ld-2.8.90.so
b7f1e000-b7f1f000 r-xp b7f1e000 00:00 0          [vdso]
b7f1f000-b7f20000 r-xp 0001a000 08:06 3178515    /lib/ld-2.8.90.so
b7f20000-b7f21000 rwxp 0001b000 08:06 3178515    /lib/ld-2.8.90.so
bfe0b000-bfe20000 rwxp bffeb000 00:00 0          [stack]
AbortedLINE LINE NOT FOUND!


```

Thanks in advance!

EDIT: I got the version I wanted installed, but it's still not working. I changed the code to the new message.

---

### Post by Wilsoz on 2009-04-17
*BUMP*

Sorry to say that I have no answers for you, only reports of pretty much the same thing with v1.51

Running 8.10 32-bit

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)
Mouse 1: Macintosh mouse button emulation
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7bce6d8]
/lib/tls/i686/cmov/libc.so.6[0xb7bcc800]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:31 2232431    /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:31 2232431    /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:31 2232431    /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
09e9c000-09f1b000 rw-p 09e9c000 00:00 0          [heap]
b5bae000-b66bc000 rw-p b5bae000 00:00 0 
b66bc000-b66de000 r-xp 00000000 08:31 2233723    /usr/lib/libaudiofile.so.0.0.2
b66de000-b66e1000 rw-p 00021000 08:31 2233723    /usr/lib/libaudiofile.so.0.0.2
b66f3000-b66f6000 r-xp 00000000 08:31 1128330    /lib/libcap.so.1.10
b66f6000-b66f7000 rw-p 00002000 08:31 1128330    /lib/libcap.so.1.10
b66f7000-b6745000 r-xp 00000000 08:31 2233451    /usr/lib/libpulse.so.0.4.1
b6745000-b6746000 r--p 0004d000 08:31 2233451    /usr/lib/libpulse.so.0.4.1
b6746000-b6747000 rw-p 0004e000 08:31 2233451    /usr/lib/libpulse.so.0.4.1
b674b000-b6754000 r-xp 00000000 08:31 2233880    /usr/lib/libesd.so.0.2.39
b6754000-b6755000 r--p 00008000 08:31 2233880    /usr/lib/libesd.so.0.2.39
b6755000-b6756000 rw-p 00009000 08:31 2233880    /usr/lib/libesd.so.0.2.39
b6756000-b6757000 r-xp 00000000 08:31 2256944    /usr/lib/ao/plugins-2/libesd.so
b6757000-b6759000 rw-p 00000000 08:31 2256944    /usr/lib/ao/plugins-2/libesd.so
b6759000-b676e000 r-xp 00000000 08:31 2233598    /usr/lib/libICE.so.6.3.0
b676e000-b676f000 rw-p 00014000 08:31 2233598    /usr/lib/libICE.so.6.3.0
b676f000-b6771000 rw-p b676f000 00:00 0 
b6771000-b67be000 r-xp 00000000 08:31 2233680    /usr/lib/libXt.so.6.0.0
b67be000-b67c2000 rw-p 0004c000 08:31 2233680    /usr/lib/libXt.so.6.0.0
b67c2000-b67d8000 r-xp 00000000 08:31 2235211    /usr/lib/libaudio.so.2.4
b67d8000-b67d9000 r--p 00015000 08:31 2235211    /usr/lib/libaudio.so.2.4
b67d9000-b67da000 rw-p 00016000 08:31 2235211    /usr/lib/libaudio.so.2.4
b67da000-b67e6000 r-xp 00000000 08:31 2233452    /usr/lib/libpulse-simple.so.0.0.1
b67e6000-b67e7000 r--p 0000b000 08:31 2233452    /usr/lib/libpulse-simple.so.0.0.1
b67e7000-b67e8000 rw-p 0000c000 08:31 2233452    /usr/lib/libpulse-simple.so.0.0.1
b67e8000-b67ea000 r-xp 00000000 08:31 2256947    /usr/lib/ao/plugins-2/libpulse.so
b67ea000-b67ec000 rw-p 00001000 08:31 2256947    /usr/lib/ao/plugins-2/libpulse.so
b67ec000-b6814000 r-xp 00000000 08:31 1128400    /lib/libpcre.so.3.12.1
b6814000-b6815000 r--p 00027000 08:31 1128400    /lib/libpcre.so.3.12.1
b6815000-b6816000 rw-p 00028000 08:31 1128400    /lib/libpcre.so.3.12.1
b6816000-b68cb000 r-xp 00000000 08:31 2233150    /usr/lib/libglib-2.0.so.0.1800.2
b68cb000-b68cc000 r--p 000b4000 08:31 2233150    /usr/lib/libglib-2.0.so.0.1800.2
b68cc000-b68cd000 rw-p 000b5000 08:31 2233150    /usr/lib/libglib-2.0.so.0.1800.2
b68cd000-b68d1000 r-xp 00000000 08:31 2233203    /usr/lib/libgthread-2.0.so.0.1800.2
b68d1000-b68d2000 r--p 00003000 08:31 2233203    /usr/lib/libgthread-2.0.so.0.1800.2
b68d2000-b68d3000 rw-p 00004000 08:31 2233203    /usr/lib/libgthread-2.0.so.0.1800.2
b68d3000-b68d6000 r-xp 00000000 08:31 2233152    /usr/lib/libgmodule-2.0.so.0.1800.2
b68d6000-b68d7000 r--p 00002000 08:31 2233152    /usr/lib/libgmodule-2.0.so.0.1800.2
b68d7000-b68d8000 rw-p 00003000 08:31 2233152    /usr/lib/libgmodule-2.0.so.0.1800.2
b68d8000-b68dd000 r-xp 00000000 08:31 2235253    /usr/lib/libartsc.so.0.0.0
b68dd000-b68de000 r--p 00004000 08:31 2235253    /usr/lib/libartsc.so.0.0.0
b68de000-b68df000 rw-p 00005000 08:31 2235253    /usr/lib/libartsc.so.0.0.0
b68df000-b68e9000 r-xp 00000000 08:31 1145327    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b68e9000-b68ea000 r--p 00009000 08:31 1145327    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b68ea000-b68eb000 rw-p 0000a000 08:31 1145327    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b68eb000-b68f4000 r-xp 00000000 08:31 1145329    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b68f4000-b68f5000 r--p 00008000 08:31 1145329    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b68f5000-b68f6000 rw-p 00009000 08:31 1145329    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b68f6000-b690b000 r-xp 00000000 08:31 1145324    /lib/tls/i686/cmov/libnsl-2.8.90.so
b690b000-b690c000 r--p 00014000 08:31 1145324    /lib/tls/i686/cmov/libnsl-2.8.90.so
b690c000-b690d000 rw-p 00015000 08:31 1145324    /lib/tls/i686/cmov/libnsl-2.8.90.so
b690d000-b690f000 rw-p b690d000 00:00 0 
b690f000-b6912000 r-xp 00000000 08:31 2256942    /usr/lib/ao/plugins-2/libalsa09.so
b6912000-b6914000 rw-p 00002000 08:31 2256942    /usr/lib/ao/plugins-2/libalsa09.so
b6914000-b691b000 r-xp 00000000 08:31 2233627    /usr/lib/libSM.so.6.0.0
b691b000-b691c000 r--p 00006000 08:31 2233627    /usr/lib/libSM.so.6.0.0
b691c000-b691d000 rw-p 00007000 08:31 2233627    /usr/lib/libSM.so.6.0.0
b691d000-b691f000 r-xp 00000000 08:31 2256946    /usr/lib/ao/plugins-2/liboss.so
b691f000-b6921000 rw-p 00001000 08:31 2256946    /usr/lib/ao/plugins-2/liboss.so
b6921000-b6924000 rw-p b6921000 00:00 0 
b6924000-b6928000 r-xp 00000000 08:31 2233650    /usr/lib/libXdmcp.so.6.0.0
b6928000-b6929000 rw-p 00003000 08:31 2233650    /usr/lib/libXdmcp.so.6.0.0
b6929000-b6940000 r-xp 00000000 08:31 2234583    /usr/lib/libxcb.so.1.0.0
b6940000-b6941000 r--p 00016000 08:31 2234583    /usr/lib/libxcb.so.1.0.0
b6941000-b6942000 rw-p 00017000 08:31 2234583    /usr/lib/libxcb.so.1.0.0
b6942000-b6943000 r-xp 00000000 08:31 2234581    /usr/lib/libxcb-xlib.so.0.0.0
b6943000-b6944000 r--p 00000000 08:31 2234581    /usr/lib/libxcb-xlib.so.0.0.0
b6944000-b6945000 rw-p 00001000 08:31 2234581    /usr/lib/libxcb-xlib.so.0.0.0
b6945000-b6947000 r-xp 00000000 08:31 2233639    /usr/lib/libXau.so.6.0.0
b6947000-b6948000 rw-p 00001000 08:31 2233639    /usr/lib/libXau.so.6.0.0
b6948000-b694f000 r-xp 00000000 08:31 1145334    /lib/tls/i686/cmov/librt-2.8.90.so
b694f000-b6950000 r--p 00007000 08:31 1145334    /lib/tls/i686/cmov/librt-2.8.90.so
b6950000-b6951000 rw-p 00008000 08:31 1145334    /lib/tls/i686/cmov/librt-2.8.90.so
b6951000-b6952000 rw-p b6951000 00:00 0 
b6952000-b6a3d000 r-xp 00000000 08:31 2232821    /usr/lib/libX11.so.6.2.0
b6a3d000-b6a3e000 r--p 000ea000 08:31 2232821    /usr/lib/libX11.so.6.2.0
b6a3e000-b6a40000 rw-p 000eb000 08:31 2232821    /usr/lib/libX11.so.6.2.0
b6a40000-b6a41000 rw-p b6a40000 00:00 0 
b6a41000-b6a4e000 r-xp 00000000 08:31 2233654    /usr/lib/libXext.so.6.4.0
b6a4e000-b6a50000 rw-p 0000c000 08:31 2233654    /usr/lib/libXext.so.6.4.0
b6a50000-b6a51000 r-xp 00000000 08:31 2265091    /usr/lib/tls/libnvidia-tls.so.180.44
b6a51000-b6a52000 rw-p 00000000 08:31 2265091    /usr/lib/tls/libnvidia-tls.so.180.44
b6a52000-b776c000 r-xp 00000000 08:31 2232479    /usr/lib/libGLcore.so.180.44
b776c000-b795e000 rwxp 00d19000 08:31 2232479    /usr/lib/libGLcore.so.180.44
b795e000-b796a000 rwxp b795e000 00:00 0 
b796a000-b797d000 r-xp 00000000 08:31 2233836    /usr/lib/libdirect-1.0.so.0.1.0
b797d000-b797e000 r--p 00012000 08:31 2233836    /usr/lib/libdirect-1.0.so.0.1.0
b797e000-b797f000 rw-p 00013000 08:31 2233836    /usr/lib/libdirect-1.0.so.0.1.0
b797f000-b7986000 r-xp 00000000 08:31 2233914    /usr/lib/libfusion-1.0.so.0.1.0
b7986000-b7987000 r--p 00006000 08:31 2233914    /usr/lib/libfusion-1.0.so.0.1.0
b7987000-b7988000 rw-p 00007000 08:31 2233914    /usr/lib/libfusion-1.0.so.0.1.0
b7988000-b7989000 rw-p b7988000 00:00 0 
b7989000-b79ed000 r-xp 00000000 08:31 2233838    /usr/lib/libdirectfb-1.0.so.0.1.0
b79ed000-b79ee000 r--p 00063000 08:31 2233838    /usr/lib/libdirectfb-1.0.so.0.1.0
b79ee000-b79ef000 rw-p 00064000 08:31 2233838    /usr/lib/libdirectfb-1.0.so.0.1.0
b79ef000-b79f1000 r-xp 00000000 08:31 1145321    /lib/tls/i686/cmov/libdl-2.8.90.so
b79f1000-b79f2000 r--p 00001000 08:31 1145321    /lib/tls/i686/cmov/libdl-2.8.90.so
b79f2000-b79f3000 rw-p 00002000 08:31 1145321    /lib/tls/i686/cmov/libdl-2.8.90.so
b79f3000-b7ab6000 r-xp 00000000 08:31 2233713    /usr/lib/libasound.so.2.0.0
b7ab6000-b7ab8000 r--p 000c2000 08:31 2233713    /usr/lib/libasound.so.2.0.0
b7ab8000-b7abb000 rw-p 000c4000 08:31 2233713    /usr/lib/libasound.so.2.0.0
b7abb000-b7ad0000 r-xp 00000000 08:31 1145332    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7ad0000-b7ad1000 r--p 00014000 08:31 1145332    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7ad1000-b7ad2000 rw-p 00Aborted

```

---

### Post by BigSilly on 2009-04-17
Have you tried [SNES 9X Gtk]("https://launchpad.net/~bearoso/+archive/ppa")? To be honest, I prefer it over ZSNES these days, though I dunno about networking...

Worth a shot either way. :)

---

### Post by Wilsoz on 2009-04-21
That's actually what I use, but I wanted to see if I could repro the problem with ZSNES.  I recommend using the 9X GTK front-end too - in the same way that Comix > CDisplay (library, preview, page-by-page thumbnails, etc.), SNES 9X > ZSNES.  But maybe I'm biased :P

---

### Post by Nevon on 2009-04-21
You could always try removing the folder .zsnes from your home directory, to see if it's a problem with the settings being carried over between your installations.

---

### Post by hikaricore on 2009-04-21
There was actually an issue with the package for zsnes in Interpid that caused such a crash.
It was easily solved by installing zsnes from this ppa:

[https://launchpad.net/~sroecker/+archive/ppa](https://launchpad.net/~sroecker/+archive/ppa)

Not sure if was ever fixed but it's a place to start.

p.s. BigSilly: please stop recommending everyone who asks about zsnes use a different emu, we get it you like snes9x, sheesh....

---

### Post by BigSilly on 2009-04-21
> **hikaricore said:**
> 
p.s. BigSilly: please stop recommending everyone who asks about zsnes use a different emu, we get it you like snes9x, sheesh....

Eh? I haven't posted on the games forums for ages, save for this thread and the Nestopia one. I don't know what you're referring to. :confused:

I like and use both emu's. I just reminded the OP that he/she has an alternative option if one doesn't work for him/her.

Have you confused me with someone else? My post history seems to suggest as much.

---

### Post by grossaffe on 2009-04-22
> **BigSilly said:**
> Have you tried [SNES 9X Gtk]("https://launchpad.net/~bearoso/+archive/ppa")? To be honest, I prefer it over ZSNES these days, though I dunno about networking...

Worth a shot either way. :)

for netplay, I use ZSNES and Znet through WINE.  Can't remember which version you need.

---

