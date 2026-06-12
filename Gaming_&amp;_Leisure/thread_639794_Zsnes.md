---
title: "Zsnes"
date: 2007-12-13
forum: Gaming &amp; Leisure
---

### Post by mr.farenheit on 2007-12-13
i try and run zsnes but all it does is bring up a window then automatically shut down.WTF?

---

### Post by Fireblend on 2007-12-13
Same thing happening to me. Any help would be greatly appreciated. Here's the terminal output:

```
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
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/sergio/.kde/socket-Abulafia.
can't create mcop directory
```

**_Edit!_** I just solved my issue with these commands, apparently it's missing a folder it needs:

```
mkdir ~/.kde/socket-`hostname`
chown -hR `id -n -g` ~/.kde
chmod 755 -R ~/.kde
```

Hopefully it will solve your issue too.

---

### Post by acoustibop on 2007-12-13
mr.farenheit, if you're not starting zsnes from a terminal, why not do so and see what output you get - as Fireblend did.

---

### Post by arbosis on 2008-12-30
I have the same problem, I tried with sudo zsnes and I got..
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
Mouse 0: Creative Creative Fatal1ty Professional Laser
Mouse 1: Macintosh mouse button emulation
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7de9558]
/lib/tls/i686/cmov/libc.so.6[0xb7de7680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:05 425322     /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:05 425322     /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:05 425322     /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
097e2000-09829000 rw-p 097e2000 00:00 0          [heap]
b6ba2000-b76d1000 rw-p b6ba2000 00:00 0 
b76d1000-b76d2000 r-xp 00000000 08:05 458346     /usr/lib/ao/plugins-2/libesd.so
b76d2000-b76d4000 rw-p 00000000 08:05 458346     /usr/lib/ao/plugins-2/libesd.so
b76d4000-b76d5000 r-xp 00000000 08:05 458345     /usr/lib/ao/plugins-2/libarts.so
b76d5000-b76d7000 rw-p 00000000 08:05 458345     /usr/lib/ao/plugins-2/libarts.so
b76d7000-b76e1000 r-xp 00000000 08:05 410187     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b76e1000-b76e2000 r--p 00009000 08:05 410187     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b76e2000-b76e3000 rw-p 0000a000 08:05 410187     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b76e3000-b76ec000 r-xp 00000000 08:05 410191     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b76ec000-b76ed000 r--p 00008000 08:05 410191     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b76ed000-b76ee000 rw-p 00009000 08:05 410191     /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b76ee000-b7703000 r-xp 00000000 08:05 410181     /lib/tls/i686/cmov/libnsl-2.8.90.so
b7703000-b7704000 r--p 00014000 08:05 410181     /lib/tls/i686/cmov/libnsl-2.8.90.so
b7704000-b7705000 rw-p 00015000 08:05 410181     /lib/tls/i686/cmov/libnsl-2.8.90.so
b7705000-b7707000 rw-p b7705000 00:00 0 
b7707000-b770e000 r-xp 00000000 08:05 410183     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b770e000-b770f000 r--p 00006000 08:05 410183     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b770f000-b7710000 rw-p 00007000 08:05 410183     /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7710000-b7713000 rw-p b7710000 00:00 0 
b7713000-b7717000 r-xp 00000000 08:05 427900     /usr/lib/libXdmcp.so.6.0.0
b7717000-b7718000 rw-p 00003000 08:05 427900     /usr/lib/libXdmcp.so.6.0.0
b7718000-b772f000 r-xp 00000000 08:05 428976     /usr/lib/libxcb.so.1.0.0
b772f000-b7730000 r--p 00016000 08:05 428976     /usr/lib/libxcb.so.1.0.0
b7730000-b7731000 rw-p 00017000 08:05 428976     /usr/lib/libxcb.so.1.0.0
b7731000-b7732000 r-xp 00000000 08:05 428972     /usr/lib/libxcb-xlib.so.0.0.0
b7732000-b7733000 r--p 00000000 08:05 428972     /usr/lib/libxcb-xlib.so.0.0.0
b7733000-b7734000 rw-p 00001000 08:05 428972     /usr/lib/libxcb-xlib.so.0.0.0
b7734000-b7736000 r-xp 00000000 08:05 427889     /usr/lib/libXau.so.6.0.0
b7736000-b7737000 rw-p 00001000 08:05 427889     /usr/lib/libXau.so.6.0.0
b7737000-b773c000 r-xp 00000000 08:05 428376     /usr/lib/libgpm.so.2.0.0
b773c000-b773d000 r--p 00004000 08:05 428376     /usr/lib/libgpm.so.2.0.0
b773d000-b773e000 rw-p 00005000 08:05 428376     /usr/lib/libgpm.so.2.0.0
b773e000-b773f000 rw-p b773e000 00:00 0 
b773f000-b77da000 r-xp 00000000 08:05 392576     /lib/libslang.so.2.1.3
b77da000-b77dd000 r--p 0009a000 08:05 392576     /lib/libslang.so.2.1.3
b77dd000-b77ea000 rw-p 0009d000 08:05 392576     /lib/libslang.so.2.1.3
b77ea000-b7820000 rw-p b77ea000 00:00 0 
b7820000-b784d000 r-xp 00000000 08:05 392526     /lib/libncurses.so.5.6
b784d000-b7850000 rw-p 0002c000 08:05 392526     /lib/libncurses.so.5.6
b7850000-b7853000 r-xp 00000000 08:05 392490     /lib/libcap.so.1.10
b7853000-b7854000 rw-p 00002000 08:05 392490     /lib/libcap.so.1.10
b7854000-b793f000 r-xp 00000000 08:05 429472     /usr/lib/libX11.so.6.2.0
b793f000-b7940000 r--p 000ea000 08:05 429472     /usr/lib/libX11.so.6.2.0
b7940000-b7942000 rw-p 000eb000 08:05 429472     /usr/lib/libX11.so.6.2.0
b7942000-b7943000 rw-p b7942000 00:00 0 
b7943000-b7958000 r-xp 0000Aborted 
```
where.. 
Mouse 0: Creative Creative Fatal1ty Professional Laser
Mouse 1: Macintosh mouse button emulation 
looks interesting.
I followed Fireblend's instructions but didn't work.

---

### Post by frenchn00b on 2008-12-30
mcop is strange.

I would recommand to compile yourself from the source code. It shouldnt be very difficult or fidn the 1.42, it goes well to to compile from source.

At the ./configure, you'll detect what is missing with the deb that ubuntu generated. You know Ubuntu is based on Unstable. So you have it : good and bad.

Good evening

---

### Post by dfreer on 2008-12-31
You actually do not have the same problem as Fireblend; As I recall, the "Missing mcop directory" was an error only occuring on a particular Ubuntu release (Gutsy I think?). 

You're particular problem has to do with running 8.10 Intrepid. For some reason, using Intrepid's GCC 4.3.2 package to compile ZSNES causes the error you are experiencing. 

So when using either the ZSNES package in the official repositories, OR when compiling the source yourself in Intrepid, the results will be the same. You need to download a binary that was NOT compiled on 8.10 (for some reason, GCC 4.3.2 in Debian Lenny compiles ZSNES with no problems).

BTW, this has been discussed multiple times on this very forum. Also, there's absolutely no need to run ZSNES with root privileges.

EDIT: Not sure why you recommend using 1.42, unless you are needing netplay. I'd actually recommend using the 1.51b source code, basically 1.51 with a patch from Nach to fix a few threading issues IIRC. 

The mcop error was resolved correctly by the above poster, basically you just need to create the folder although there is a very good thread about that issue somewhere on this site.

As for compiling ZSNES, **sudo apt-get build-dep zsnes** should download most of the build dependencies if not all of them.

---

