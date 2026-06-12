---
title: "Ubuntu 8.10, ZSNES stoped working"
date: 2008-11-09
forum: Gaming &amp; Leisure
---

### Post by mac-duff on 2008-11-09
Hi,
after my upgrade to 8.10 my ZNES stoped working. It tells me about permission but it worked ever before. What can I do?
Thx
 zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7df3558]
/lib/tls/i686/cmov/libc.so.6[0xb7df1680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:01 43296      /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:01 43296      /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:01 43296      /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
091cf000-09219000 rw-p 091cf000 00:00 0          [heap]
b6cac000-b77db000 rw-p b6cac000 00:00 0 
b77db000-b77fd000 r-xp 00000000 08:01 41707      /usr/lib/libaudiofile.so.0.0.2
b77fd000-b7800000 rw-p 00021000 08:01 41707      /usr/lib/libaudiofile.so.0.0.2
b7800000-b7809000 r-xp 00000000 08:01 40029      /usr/lib/libesd.so.0.2.39
b7809000-b780a000 r--p 00008000 08:01 40029      /usr/lib/libesd.so.0.2.39
b780a000-b780b000 rw-p 00009000 08:01 40029      /usr/lib/libesd.so.0.2.39
b781d000-b7845000 r-xp 00000000 08:01 24074      /lib/libpcre.so.3.12.1
b7845000-b7846000 r--p 00027000 08:01 24074      /lib/libpcre.so.3.12.1
b7846000-b7847000 rw-p 00028000 08:01 24074      /lib/libpcre.so.3.12.1
b7847000-b78fc000 r-xp 00000000 08:01 40046      /usr/lib/libglib-2.0.so.0.1800.2
b78fc000-b78fd000 r--p 000b4000 08:01 40046      /usr/lib/libglib-2.0.so.0.1800.2
b78fd000-b78fe000 rw-p 000b5000 08:01 40046      /usr/lib/libglib-2.0.so.0.1800.2
b78fe000-b7902000 r-xp 00000000 08:01 40106      /usr/lib/libgthread-2.0.so.0.1800.2
b7902000-b7903000 r--p 00003000 08:01 40106      /usr/lib/libgthread-2.0.so.0.1800.2
b7903000-b7904000 rw-p 00004000 08:01 40106      /usr/lib/libgthread-2.0.so.0.1800.2
b7904000-b7907000 r-xp 00000000 08:01 40088      /usr/lib/libgmodule-2.0.so.0.1800.2
b7907000-b7908000 r--p 00002000 08:01 40088      /usr/lib/libgmodule-2.0.so.0.1800.2
b7908000-b7909000 rw-p 00003000 08:01 40088      /usr/lib/libgmodule-2.0.so.0.1800.2
b7917000-b7919000 r-xp 00000000 08:01 187314     /usr/lib/ao/plugins-2/liboss.so
b7919000-b791b000 rw-p 00001000 08:01 187314     /usr/lib/ao/plugins-2/liboss.so
b791b000-b791e000 r-xp 00000000 08:01 24041      /lib/libcap.so.1.10
b791e000-b791f000 rw-p 00002000 08:01 24041      /lib/libcap.so.1.10
b791f000-b796d000 r-xp 00000000 08:01 40966      /usr/lib/libpulse.so.0.4.1
b796d000-b796e000 r--p 0004d000 08:01 40966      /usr/lib/libpulse.so.0.4.1
b796e000-b796f000 rw-p 0004e000 08:01 40966      /usr/lib/libpulse.so.0.4.1
b796f000-b797b000 r-xp 00000000 08:01 40973      /usr/lib/libpulse-simple.so.0.0.1
b797b000-b797c000 r--p 0000b000 08:01 40973      /usr/lib/libpulse-simple.so.0.0.1
b797c000-b797d000 rw-p 0000c000 08:01 40973      /usr/lib/libpulse-simple.so.0.0.1
b797d000-b7992000 r-xp 00000000 08:01 41551      /usr/lib/libICE.so.6.3.0
b7992000-b7993000 rw-p 00014000 08:01 41551      /usr/lib/libICE.so.6.3.0
b7993000-b7995000 rw-p b7993000 00:00 0 
b7995000-b79e2000 r-xp 00000000 08:01 41664      /usr/lib/libXt.so.6.0.0
b79e2000-b79e6000 rw-p 0004c000 08:01 41664      /usr/lib/libXt.so.6.0.0
b79e6000-b79fc000 r-xp 00000000 08:01 42196      /usr/lib/libaudio.so.2.4
b79fc000-b79fd000 r--p 00015000 08:01 42196      /usr/lib/libaudio.so.2.4
b79fd000-b79fe000 rw-p 00016000 08:01 42196      /usr/lib/libaudio.so.2.4
b79fe000-b79ff000 r-xp 00000000 08:01 187312     /usr/lib/ao/plugins-2/libesd.so
b79ff000-b7a01000 rw-p 00000000 08:01 187312     /usr/lib/ao/plugins-2/libesd.so
b7a01000-b7a06000 r-xp 00000000 08:01 42180      /usr/lib/libartsc.so.0.0.0
b7a06000-b7a07000 r--p 00004000 08:01 42180      /usr/lib/libartsc.so.0.0.0
b7a07000-b7a08000 rw-p 00005000 08:01 42180      /usr/lib/libartsc.so.0.0.0
b7a08000-b7a09000 r-xp 00000000 08:01 187308     /usr/lib/ao/plugins-2/libarts.so
b7a09000-b7a0b000 rw-p 00000000 08:01 187308     /usr/lib/ao/plugins-2/libarts.so
b7a0b000-b7a0e000 r-xp 00000000 08:01 187307     /usr/lib/ao/plugins-2/libalsa09.so
b7a0e000-b7a10000 rw-p 00002000 08:01 187307     /usr/lib/ao/plugins-2/libalsa09.so
b7a10000-b7a1a000 r-xp 00000000 08:01 68292      /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7a1a000-b7a1b000 r--p 0000Aborted

---

### Post by Zeromaru on 2008-11-09
Hmm, I get the exact same error. Tried turning off Compiz, same thing.

---

### Post by dfreer on 2008-11-09
There's posts about this in this forums and in the ZSNES forums, it's a known issue. Use a binary that wasn't compiled using Ubuntu's GCC 4.3.2 would be my quick advice :D

---

### Post by VitaminBB on 2008-11-10
I never was totally satisfied with ZSNES ...

I installed the latest snes9x using the windows executable in wine, works PERFECTLY!

No lag at all when playing and I can customize my controller ten times better then ZSNES ever could ...

My advice, use Snes9x and wine, works great

---

### Post by mister_k81 on 2008-11-10
> **VitaminBB said:**
> I never was totally satisfied with ZSNES ...

I installed the latest snes9x using the windows executable in wine, works PERFECTLY!


Why use wine? When there is a really good native port here: 

[http://www.snes9x.com/phpbb2/viewtopic.php?p=22874](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874)

It works great in intrepid. but make sure to also install libportaudio2 from the repos.


And as for ZSNES, I couldn't get it to compile in intrepid either. and the version in the repos is useless... Right now, I'm using the compiled binary that dfreer posted in this thread, which works fine:  [http://ubuntuforums.org/showthread.php?t=960649&highlight=zsnes](http://ubuntuforums.org/showthread.php?t=960649&highlight=zsnes)

So thanks for that. :)

---

### Post by Mamsaac on 2008-11-14
This is the worst thing I've seen in Intrepid =( Other than that, everything is perfect, but I want my ZSNES back =(

---

### Post by dfreer on 2008-11-14
> **Mamsaac said:**
> This is the worst thing I've seen in Intrepid =( Other than that, everything is perfect, but I want my ZSNES back =(

Just download a working version of ZSNES as we stated above, or perhaps file a bug report against GCC 4.3.2 in Ubuntu, as GCC 4.3.2 in Debian compiles ZSNES just fine.

---

### Post by fabbaz on 2008-11-17
i just had the same problems, and tried and found out that the gutsy version is working on my intrepid install.
(i didn't use hardy but i remembered zsnes running perfectly well on gutsy... oh, the days... ;) )
long story short:
[http://packages.ubuntu.com/gutsy/i386/zsnes/download](http://packages.ubuntu.com/gutsy/i386/zsnes/download)
here you get the zsnes deb from the gutsy repositories, just make sure you uninstall any version you already have prior to installing.
( sudo apt-get remove zsnes 
then download
then doubleclick the downloaded deb)
now works like a charm. yay!

---

### Post by BigSilly on 2008-11-17
I had the same problems with the version in repository. It just doesn't work. I used this package below that I found on Launchpad, and it's been fine for me with Intrepid. Hope it's useful for you guys here too. :)

---

### Post by shufei4520564 on 2008-11-17
how can i make [runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php) fast??

---

### Post by eltoozero on 2008-11-25
Sweet, yes in fact installing the Gutsy package for zsnes works.

Package download here: [http://packages.ubuntu.com/gutsy/i386/zsnes/download]("http://packages.ubuntu.com/gutsy/i386/zsnes/download")

You should freeze the package version using Synaptic so you're not stuck with software update killing your newly working zsnes.

System->Administration->Synaptic->
Select the packages you don't want to update
From packages menu -> select "Lock Version"
~or~
aptitude hold pkgname

Instructions stolen from: [http://ubuntuforums.org/showthread.php?p=1324502]("http://ubuntuforums.org/showthread.php?p=1324502")

:)

---

### Post by andlinux on 2008-12-11
Well, it's not working here.

I get this message:

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  11
  Current serial number in output stream:  11
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb795d7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb795d96e]
#2 /usr/lib/libX11.so.6 [0xb79a5619]
#3 /usr/lib/libX11.so.6(XSync+0x25) [0xb7999625]
#4 /usr/lib/libSDL-1.2.so.0 [0xb7f35b25]
#5 /usr/lib/libSDL-1.2.so.0 [0xb7f3ebbb]
#6 /usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x50) [0xb7f2c940]
#7 /usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x55) [0xb7f017d5]
#8 zsnes [0x82ee6cc]
#9 /usr/lib/libX11.so.6 [0xb799dd4e]
#10 /usr/lib/libSDL-1.2.so.0 [0xb7f3e4f6]
#11 /usr/lib/libX11.so.6(_XError+0x109) [0xb799def9]
#12 /usr/lib/libX11.so.6(_XReply+0x22e) [0xb79a646e]
#13 /usr/lib/libGL.so.1 [0xb7e9fd07]
#14 /usr/lib/libGL.so.1 [0xb7e81375]
#15 /usr/lib/libGL.so.1(glXChooseVisual+0x37) [0xb7e7e357]
#16 /usr/lib/libSDL-1.2.so.0 [0xb7f3ace1]
#17 /usr/lib/libSDL-1.2.so.0 [0xb7f41046]
#18 /usr/lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1f0) [0xb7f2d900]
#19 zsnes [0x82f13b1]
Segmentatiefout

```

---

### Post by maddog46113 on 2008-12-11
I downloaded a stand alone works perfectly.

---

### Post by |Jasp| on 2009-01-06
Thank you Fabbaz!  The very first North American mirror did the trick just fine.

---

### Post by gdbutcher on 2009-01-18
Thanks eltoozero your suggestion worked a hell of a lot better than mine. I resorted to running the windows version through wine. The linux version performs much better :)

---

