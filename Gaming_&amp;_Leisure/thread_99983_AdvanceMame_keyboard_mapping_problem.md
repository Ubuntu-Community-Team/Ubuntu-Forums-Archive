---
title: "AdvanceMame keyboard mapping problem"
date: 2005-12-06
forum: Gaming &amp; Leisure
---

### Post by fif on 2005-12-06
Hi folks,

I build the latest AdvanceMame package and it is running ok with sdl video configuration. I have a latin-fr keyboard. As the default layout is US english, some keys of my keyboard have no effect.  I wanted to get latin key codes using avdk, but my compiled version only supports raw, event and svga_lib.
I did not install svga_lib and neither raw nor event are compatible with X11.
Checking the avdk makefile, sdl is not taken into account despite I explicitely asked for sdl support at configure... tried quickly to add SDL support in the makefile (extra flags, link dirs and 1 source file) but I got a linker warning and gave up for the time being... :confused:

---

