---
title: "Bigger window in D2"
date: 2007-04-29
forum: Gaming &amp; Leisure
---

### Post by adza on 2007-04-29
Hi there, well i've managed to get Diablo2 running on feisty, all sound and graphics working well... So far, every post i read looking for this solution seems to want to run D2 in window... well mine is running in a window.. i just need to know how to make the window bigger? There doesn't seem to be any options in game for screen res.... see attached screenshot.. it's like playing on a postage stamp! still... i'm running, but if anyone could tell me how to increase the size of this window, i would be appreciative...

p.s. i've already set the virtual desktop option to be 1680 * 1050 (my res).. still, no effect on the game...

---

### Post by adza on 2007-04-30
*****bump*****

---

### Post by aurelix on 2007-04-30
Ctrl+Alt++ / Ctrl+Alt+-  switches through the resolutions Xorg knows about.
you can also open a console window and use xrandr:
```
xrandr
``` gives a list of possible resolutions
```
xrandr -s 5
```  switches resolution (substitute the number of the list entry you want for the 5)

You will probably have to use a widescreen res like 1024x600 or similar.

A more sophisticated solution is to add more Layout and Screen sections to your /etc/X11/xorg.conf. Tutorials can be found on the net. then you can run your games in a separate X server (that's the way I prefer).

---

### Post by adza on 2007-04-30
thanks aurelix! i'm working at the moment (which means i'm stuck in the windows world...) but will get onto this as soon as i'm done :)

---

### Post by disturbedite on 2007-04-30
if i understand this correctly, i've got bad news for ya.  d2 only runs in 800x600 (max).  can't change it with wine.  you can specify your virtual desktop, but that doesn't effect any games' "built in" resolutions.

---

