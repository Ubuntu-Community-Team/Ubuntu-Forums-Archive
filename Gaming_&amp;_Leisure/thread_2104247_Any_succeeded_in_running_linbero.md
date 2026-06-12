---
title: "Any succeeded in running linbero?"
date: 2013-01-12
forum: Gaming &amp; Leisure
---

### Post by zerothis on 2013-01-12
I came accros this retro Q*Bert clone Linberto [http://www.grigna.com/diego/linux/linberto/](http://www.grigna.com/diego/linux/linberto/)
Compiles and in stalls fine, also installs with alien. Little problems with it using /dev/dsp and only running as root but those are not a priority.

Main problem is this, it seems to hang my system but its actually running something. My screen flashes blue almost to quickly to be seen then the text seems a bit off from its usual color. It outputs this:
```
Using VESA Driver, 16384. VBE3
svgalib 1.4.3
```

I can get no response from my system until I ctrl-alt-esc or press Q (see, its not actually hanging). Then it outputs:
```
Linberto - version 1.0.5
Copyright (C) 1999-2001 Diego Javier Grigna <diego@grigna.com>
Linberto is covered by the GNU General Public License
$
```

My virtual terminal is 160x54 which might be the problem but I want to investigate other things before changing back to the default. I've added and tested 320x200 mode in my xorg server although I'm 99.9% certain this is meaningless to an svgalib application.

---

