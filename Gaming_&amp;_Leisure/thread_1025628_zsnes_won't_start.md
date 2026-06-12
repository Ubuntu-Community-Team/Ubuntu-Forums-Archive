---
title: "zsnes won't start"
date: 2008-12-30
forum: Gaming &amp; Leisure
---

### Post by Trixilver on 2008-12-30
I have never installed zsnes before and the other day I decided to try it but when I launch it nothing happens. Here's what it tells me if I run through terminal:

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
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d47558]
/lib/tls/i686/cmov/libc.so.6[0xb7d45680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 4251807    /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 4251807    /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 4251807    /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
09526000-09570000 rw-p 09526000 00:00 0          [heap]
b6c2a000-b7759000 rw-p b6c2a000 00:00 0 
b7759000-b7781000 r-xp 00000000 08:01 3317873    /lib/libpcre.so.3.12.1
b7781000-b7782000 r--p 00027000 08:01 3317873    /lib/libpcre.so.3.12.1
b7782000-b7783000 rw-p 00028000 08:01 3317873    /lib/libpcre.so.3.12.1
b7783000-b7838000 r-xp 00000000 08:01 4252467    /usr/lib/libglib-2.0.so.0.1800.2
b7838000-b7839000 r--p 000b4000 08:01 4252467    /usr/lib/libglib-2.0.so.0.1800.2
b7839000-b783a000 rw-p 000b5000 08:01 4252467    /usr/lib/libglib-2.0.so.0.1800.2
b783a000-b783e000 r-xp 00000000 08:01 4254753    /usr/lib/libgthread-2.0.so.0.1800.2
b783e000-b783f000 r--p 00003000 08:01 4254753    /usr/lib/libgthread-2.0.so.0.1800.2
b783f000-b7840000 rw-p 00004000 08:01 4254753    /usr/lib/libgthread-2.0.so.0.1800.2
b7840000-b7843000 r-xp 00000000 08:01 4252472    /usr/lib/libgmodule-2.0.so.0.1800.2
b7843000-b7844000 r--p 00002000 08:01 4252472    /usr/lib/libgmodule-2.0.so.0.1800.2
b7844000-b7845000 rw-p 00003000 08:01 4252472    /usr/lib/libgmodule-2.0.so.0.1800.2
b7845000-b784a000 r-xp 00000000 08:01 4253408    /usr/lib/libartsc.so.0.0.0
b784a000-b784b000 r--p 00004000 08:01 4253408    /usr/lib/libartsc.so.0.0.0
b784b000-b784c000 rw-p 00005000 08:01 4253408    /usr/lib/libartsc.so.0.0.0
b784c000-b786e000 r-xp 00000000 08:01 4253422    /usr/lib/libaudiofile.so.0.0.2
b786e000-b7871000 rw-p 00021000 08:01 4253422    /usr/lib/libaudiofile.so.0.0.2
b787e000-b7881000 r-xp 00000000 08:01 4276712    /usr/lib/ao/plugins-2/libalsa09.so
b7881000-b7883000 rw-p 00002000 08:01 4276712    /usr/lib/ao/plugins-2/libalsa09.so
b7883000-b7886000 r-xp 00000000 08:01 3317802    /lib/libcap.so.1.10
b7886000-b7887000 rw-p 00002000 08:01 3317802    /lib/libcap.so.1.10
b7887000-b78d5000 r-xp 00000000 08:01 4252081    /usr/lib/libpulse.so.0.4.1
b78d5000-b78d6000 r--p 0004d000 08:01 4252081    /usr/lib/libpulse.so.0.4.1
b78d6000-b78d7000 rw-p 0004e000 08:01 4252081    /usr/lib/libpulse.so.0.4.1
b78d8000-b78d9000 r-xp 00000000 08:01 4276713    /usr/lib/ao/plugins-2/libarts.so
b78d9000-b78db000 rw-p 00000000 08:01 4276713    /usr/lib/ao/plugins-2/libarts.so
b78db000-b78e4000 r-xp 00000000 08:01 4253598    /usr/lib/libesd.so.0.2.39
b78e4000-b78e5000 r--p 00008000 08:01 4253598    /usr/lib/libesd.so.0.2.39
b78e5000-b78e6000 rw-p 00009000 08:01 4253598    /usr/lib/libesd.so.0.2.39
b78e6000-b78e7000 r-xp 00000000 08:01 4276714    /usr/lib/ao/plugins-2/libesd.so
b78e7000-b78e9000 rw-p 00000000 08:01 4276714    /usr/lib/ao/plugins-2/libesd.so
b78e9000-b78fe000 r-xp 00000000 08:01 4253280    /usr/lib/libICE.so.6.3.0
b78fe000-b78ff000 rw-p 00014000 08:01 4253280    /usr/lib/libICE.so.6.3.0
b78ff000-b7901000 rw-p b78ff000 00:00 0 
b7901000-b794e000 r-xp 00000000 08:01 4253366    /usr/lib/libXt.so.6.0.0
b794e000-b7952000 rw-p 0004c000 08:01 4253366    /usr/lib/libXt.so.6.0.0
b7952000-b7968000 r-xp 00000000 08:01 4253420    /usr/lib/libaudio.so.2.4
b7968000-b7969000 r--p 00015000 08:01 4253420    /usr/lib/libaudio.so.2.4
b7969000-b796a000 rw-p 00016000 08:01 4253420    /usr/lib/libaudio.so.2.4
b796a000-b7976000 r-xp 00000000 08:01 4252082    /usr/lib/libpulse-simple.so.0.0.1
b7976000-b7977000 r--p 0000b000 08:01 4252082    /usr/lib/libpulse-simple.so.0.0.1
b7977000-b7978000 rw-p 0000c000 08:01 4252082    /usr/lib/libpulse-simple.so.0.0.1
b7978000-b797a000 r-xp 00000000 08:01 4276717    /usr/lib/ao/plugins-2/libpulse.so
b797a000-b797c000 rw-p 00001000 08:01 4276717    /usr/lib/ao/plugins-2/libpulse.so
b797c000-b7986000 r-xp 00000000 08:01 3335334    /lib/tls/i686/Aborted
```

I'm running Linux Mint 6 (Ubuntu 8.10). Any help?

---

### Post by frenchn00b on 2008-12-30
same here:

mcop is strange.

I would recommand to compile yourself from the source code. It shouldnt be very difficult or fidn the 1.42, it goes well to to compile from source.

At the ./configure, you'll detect what is missing with the deb that ubuntu generated. You know Ubuntu is based on Unstable. So you have it : good and bad.

Good evening

---

### Post by dfreer on 2008-12-31
Wow, does no one use the search feature anymore? There's another ZSNES thread on the same page dealing with this issue.

You are not experiencing the mcop error as the above poster stated; that only affected certain older releases of Ubuntu IIRC. The solution to your problem is to obtain a binary of ZSNES that was NOT compiled using Ubuntu Intrepid's GCC 4.3

Just read this thread if there is anymore confusion: [http://board.zsnes.com/phpBB2/viewtopic.php?t=12093](http://board.zsnes.com/phpBB2/viewtopic.php?t=12093)

---

### Post by BigSilly on 2008-12-31
> **dfreer said:**
> Wow, does no one use the search feature anymore? There's another ZSNES thread on the same page dealing with this issue.

You are not experiencing the mcop error as the above poster stated; that only affected certain older releases of Ubuntu IIRC. The solution to your problem is to obtain a binary of ZSNES that was NOT compiled using Ubuntu Intrepid's GCC 4.3

Just read this thread if there is anymore confusion: [http://board.zsnes.com/phpBB2/viewtopic.php?t=12093](http://board.zsnes.com/phpBB2/viewtopic.php?t=12093)

Without wishing to be rude to newcomers, I have to +1 this. I have lost count of how many posts there have been about this issue. All someone has to do is have a quick look using the search function. 

I placed a properly functioning ZSNES package in one of my posts. See if you can find it.

---

