---
title: "Steam not loading on Opensource Drivers"
date: 2015-02-23
forum: Gaming &amp; Leisure
---

### Post by caseyhunter on 2015-02-23
Hello! 
Since I try to support the opensource drivers I have switched to only using them on my Ubuntu partition, but steam refuses to open when using opensource graphics drivers.
When lauching from the terminal I get the following errors:
Running Steam on ubuntu 14.10 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1422054110)
libGL error: unable to load driver: radeonsi_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: radeonsi
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast

Any help is appreciated!

---

### Post by oldrocker99 on 2015-02-23
This may have a solution:[https://github.com/anyc/steam-overlay/issues/102](https://github.com/anyc/steam-overlay/issues/102). Good luck.

---

### Post by R33D3M33R on 2015-02-24
I have been using this trick with success: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

---

### Post by caseyhunter on 2015-03-02
> **R33D3M33R said:**
> I have been using this trick with success: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

This works to allow me to access steam with opensource drivers, only issue is I'm getting some weird color scheme on TF2, colors are splattered everywhere, very glitchy looking.

---

