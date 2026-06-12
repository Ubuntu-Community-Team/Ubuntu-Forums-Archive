---
title: "Can't change screen resolution and refresh rate in XFCE"
date: 2007-11-23
forum: Desktop Environments
---

### Post by venil82 on 2007-11-23
My monitor supports 1024x768@85Hz
default setting of vertrefresh in /etc/X11/xorg.conf gives resolution 1024x768@60Hz
so i changed it to be constant :

```
vertrefresh 85
```

after restarting x server, i get 85 Hz but the resolution went down to 800*600, even though i have "1024x768" in my conf file

---

### Post by Happy_Man on 2007-11-23
Well, yes, xorg.conf still doesn't think that you have a monitor that can *do* 1024x768 at 80 Hz. You may have to force set your resolution also.

---

### Post by venil82 on 2007-11-23
so how do i **force** it?

---

### Post by jav_ on 2007-11-24
i have a similar problem..bump

---

### Post by derby007 on 2007-11-24
Get the specifics of your monitor: ie. 
•	Horizontal frequency: 30 to 70 kHz 
•	Vertical frequency: 50 to 160 Hz 

Then add them to xorg.conf:
Section "Monitor"
[INDENT]Identifier	"Generic Monitor"[/INDENT]
[INDENT]Option	"DPMS"[/INDENT]
[INDENT]Horizsync	30-70		#28-51[/INDENT]
[INDENT]Vertrefresh	50-160		#43-60[/INDENT]
EndSection

And have the mode you require:
SubSection "Display"
[INDENT]Depth	24[/INDENT]
[INDENT]Modes     "1152x864"    "1024x768" [/INDENT]
EndSubSection

---

