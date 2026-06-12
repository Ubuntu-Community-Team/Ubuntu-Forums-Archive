---
title: "Cairo-Dock V2 uses 95% CPU"
date: 2009-06-01
forum: Desktop Environments
---

### Post by wrongnumber on 2009-06-01
Hi, 
jaunty user here. I'm using OpenGL version: 2.1.2 NVIDIA 173.14.16
for NVDIA FX 5700VE. Compiz enabled. 
Cairo-dock with opengl uses too much CPU resource. 
Is there any workaround or is my vga card simply too old?

Thanks in advance,

---

### Post by fabounet on 2009-06-02
try deactivating all applets and plug-ins, restart it.
if it continues, then probably the answer is yes, and you should use the cairo mode.

---

### Post by wrongnumber on 2009-06-02
Thanks for the reply, fabounet.
The dock uses lower ressource after I turn off the applets and plugins and restart the dock. 
I notice, that the clock applet was the culprit. Every time I activate this applet in opengl-mode, cairo-dock drains my cpu ressource. Really don't know what happens there. 
Any clue?

---

### Post by zero1one0 on 2009-06-02
why dont you just remove cairo dock and use a panel instead
when you add a panel go into properties
uncheck expand
and check autohide
add your launchers
and then you have something that looks like a dock
oh and choose what side of the screen its on to

---

### Post by fabounet on 2009-06-03
ok, in this applet there is an option to make seconds run smoothly.
maybe your drivers don't like it.
so open the config of CLock, and either :
- set the smooth value to 0
- or deactivate the option that shows the seconds.

---

### Post by wrongnumber on 2009-06-03
@zero1one0: thanks for the info. I used the panel as a dock before, but I guess I prefer cairo-dock instead of panel. Again, many thanks!

@fabounet: It's just as you said. I deactivated the show-second-option and the dock's cpu usage stay below 3% in standby. The cpu usage jumps up to 20-30% temporarily if hover my mouse over the dock, but I think it's normal. Thanks a bunch for the help and the dock!

---

### Post by fabounet on 2009-06-04
GeForce5 are old cards and their drivers are far from perfect, that may explain the CPU load.
with a mere GeForce7 the dock is around 0.3% at rest and 10% with a lot of effects.

---

