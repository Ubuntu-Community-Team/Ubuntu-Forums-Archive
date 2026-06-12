---
title: "Wargus installation"
date: 2007-10-02
forum: Gaming &amp; Leisure
---

### Post by balornt on 2007-10-02
I have searched forums all over the web to try to install this Stratagus mod. I managed to install Stratagus and build Wargus (at least extracting the files from the cd). But when I try to run it:

balornt@balornt-laptop:~/Desktop/game stuff/wargus-2.2.4$ stratagus -d data.wc2/Stratagus default config file loading ...

Can't open file 'preferences.lua': No such file or directory
... ready!

Stratagus V2.2.4, (c) 1998-2006 by The Stratagus Project.
  written by Lutz Sammer, Fabrice Rossi, Vladi Shabanski, Patrice Fortier,
Jon Gabrielson, Andreas Arens, Nehal Mistry, Jimmy Salmon, and others.
        ([http://stratagus.org](http://stratagus.org))
Compile options ZLIB BZ2LIB VORBIS MIKMOD 

Stratagus may be copied only under the terms of the GNU General Public License
which may be found in the Stratagus source kit.

DISCLAIMER:
This software is provided as-is.  The author(s) can not be held liable for any
damage that might arise from the use of this software.
Use it at your own risk.

Couldn't initialize SDL: No available video device
balornt@balornt-laptop:~/Desktop/game stuff/wargus-2.2.4$

My video card is an Intel 915GM (I know it sucks, it's my laptop)

---

### Post by balornt on 2007-10-05
figured it out, needs xlib too

---

