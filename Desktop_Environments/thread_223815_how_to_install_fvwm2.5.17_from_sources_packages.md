---
title: "how to install fvwm2.5.17 from sources packages"
date: 2006-07-27
forum: Desktop Environments
---

### Post by yuzifu on 2006-07-27
hi all, my english is so poor, but i compile the fvwm 2.5.17 have some error and i can't get help in my language, so i logging on this Forums in english.

i download the sources packages from [www.fvwm.org](www.fvwm.org)
then uncompress the fvwm-2.5.17.tar.gz in my space

#cd fvwm-2.5.17
#./configure --x-includes=/usr/include/X11/ --x-libraries=/usr/lib/x11/
.
.
.
.
.
.
FVWM Configuration:

  Version:     2.5.17

  Executables: /usr/local/bin
  Man pages:   /usr/local/man
  Modules:     /usr/local/libexec/fvwm/2.5.17
  Data files:  /usr/local/share/fvwm
  Perl lib:    /usr/local/share/fvwm/perllib
  Locale msg:  /usr/local/share/locale  ar de fr sv_SE zh_CN

  With Asian bi-direct. text support? no: No fribidi-config found in PATH
  With Gettext Native Lang support?   yes (libc)
  With GTK+ required for FvwmGtk?     no: Failed to detect GTK, see config.log
  With Iconv support?                 yes (from C library)
  With Mouse strokes (gestures)?      no: Can't find working libstroke
  With PNG image support?             no: Can't find working libpng
  With ReadLine sup. in FvwmConsole?  no: Can't find working libreadline
  With RPlay support in FvwmEvent?    no: Can't find working librplay
  With Shaped window support?         no: Failed to detect Shape extension
  With Shared memory for XImage?      no: Can't detect MIT Shared Memory ext.
  With Session Management support?    no: Failed to detect libSM
  With Xinerama multi-head support?   no: Failed to detect libXinerama
  With Xft anti-alias font support?   no: Can't detect freetype2 >= 6.1.0/2.0.6
  With XPM image support?             no: Can't find working libXpm
  With Xrender image support?         no: Failed to detect libXrender

See INSTALL.fvwm for the description of what this may mean.
#

how did i install fvwm 2.5.17 from sources packages?
thanks!

---

### Post by yuzifu on 2006-07-27
up

---

### Post by jpkotta on 2006-07-29
You need dev packages.  I couldn't tell you exactly which ones to get, because I installed them so long ago, but I can tell you how to figure it out yourself.

Just go down the list and install -dev packages until configure says a feature is configured.  For example, install libreadline-dev to get readline support (this is used in FvwmConsole and is very convenient).  To find which packages to install, just search for them in synaptic, e.g. search for "readline dev" and you'll get libreadline-dev as a result.  I'm pretty sure all of the packages you need to build end in "-dev".  After installing libreadline-dev, run configure again, and it should say readline is supported.  Then just continue in the same way for all of the features you want.

---

