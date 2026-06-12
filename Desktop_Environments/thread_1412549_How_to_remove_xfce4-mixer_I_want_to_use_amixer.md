---
title: "How to remove xfce4-mixer? I want to use amixer"
date: 2010-02-21
forum: Desktop Environments
---

### Post by cd-r80 on 2010-02-21
If I remove it from panel I only got:

xfce4-mixer-plu defunct

and then adding

amixer slider gives 

amixer defunct
amixer defunct....

9.10 Xubuntu.

---

### Post by Hero of Time on 2010-02-21
Couldn't you just change the properties of the mixer applet to start amixer instead of xfce4-mixer? Both control the same mixer, so I wonder why you want to change it.
In case it's a terminal volume control, use 'xfce4-terminal -x amixer' for the run command.

---

### Post by cd-r80 on 2010-02-21
Not possible because I want use generic-slider plugin to control my master volume.

[http://goodies.xfce.org/projects/panel-plugins/xfce4-generic-slider](http://goodies.xfce.org/projects/panel-plugins/xfce4-generic-slider)

" While it can do much more, this was originally designed to bring back the volume slider which some people miss from Xfce 4.4. "

---

### Post by Hero of Time on 2010-02-21
Ah, I see. You want a visual representation of the volume level. It is already shown on the icon itself, for me anyway. But a bar next to the volume icon can be more useful, as well as an actual slider like on Gnome.

---

### Post by cd-r80 on 2010-02-21
Yes I put it next to the volume icon, but then what happens is:

3382 user  20   0     0    0    0 Z    0  0.0   0:00.01 amixer <defunct> 

slider slides down...

---

