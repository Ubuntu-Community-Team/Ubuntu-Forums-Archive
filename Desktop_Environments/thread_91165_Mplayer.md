---
title: "Mplayer"
date: 2005-11-16
forum: Desktop Environments
---

### Post by Jaakdedraak on 2005-11-16
when i try to install Mplayer i get this message, does anyone know what is is?
Or better yet, how can i solve it?
sorry, i'm kinda new with this Linux thing

jan@kamer18:~/MPlayer$ ./configure --enable-gui
Detected operating system: Linux
Detected host architecture: i386
Checking for cc version ... not found
Checking for gcc version ... not found
Checking for gcc-3.4 version ... not found
Checking for gcc-3.3 version ... 3.3.6, ok
Checking for host cc ... gcc-3.3
Checking for CPU vendor ... GenuineIntel (15:2:4)
Checking for CPU type ...  Intel(R) Pentium(R) 4 Mobile CPU 1.80GHz
Checking for GCC & CPU optimization abilities ... Your gcc-3.3 does not even support "i386" for '-march' and '-mcpu'.
error
Checking for kernel support of mmx ... failed
It seems that your kernel does not correctly support mmx.
To use mmx extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of mmx2 ... failed
It seems that your kernel does not correctly support mmx2.
To use mmx2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse ... failed
It seems that your kernel does not correctly support sse.
To use sse extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for kernel support of sse2 ... failed
It seems that your kernel does not correctly support sse2.
To use sse2 extensions in MPlayer, you have to upgrade/recompile your kernel!
Checking for mtrr support ... yes
Checking for assembler support of -pipe option ... no
Checking for assembler (as 2.16.1) ... ok
Checking for Linux kernel version ... 2.6.12-9-386, ok
Checking for mplayer binary name ... mplayer
Checking for awk ... mawk
Checking for extra headers ... none
Checking for extra libs ... none
Checking for -lposix ... no
Checking for -lm ... no
Checking for i18n ... no
Checking for iconv ... no
Checking for langinfo ... no
Checking for language ... using en (man pages:  en)
Checking for enable sighandler ... yes
Checking for runtime cpudetection ... no
Checking for restrict keyword ... none
Checking for __builtin_expect ... no
Checking for kstat ... no
Checking for posix4 ... no
Checking for lrintf ... no
Checking for nanosleep ... no
Checking for socklib ... no
Checking for inet_pton() ... no (=> i'll try inet_aton next)
Checking for inet_aton() ... no (=> network support disabled)
Checking for inttypes.h (required) ... no
Checking for bitypes.h (inttypes.h predecessor) ...
Error: Cannot find header either inttypes.h or bitypes.h (see DOCS/HTML/en/faq.html).

Check "configure.log" if you do not understand why it failed.

---

### Post by nrwilk on 2005-11-16
Looks like the either inttypes.h or bitypes.h is required to compile Mplayer.

I looked in adept to see if they reside in the repositories, but I didn't see either one.

---

### Post by rusi_pathan on 2005-11-16
Try to install glibc-devel first

---

