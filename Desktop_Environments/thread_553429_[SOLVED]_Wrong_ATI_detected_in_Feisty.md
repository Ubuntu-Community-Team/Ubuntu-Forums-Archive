---
title: "[SOLVED] Wrong ATI detected in Feisty"
date: 2007-09-17
forum: Desktop Environments
---

### Post by WolfLust on 2007-09-17
Hello all,

I have recently installed Feisty and when I do: glxinfo | egrep 'OpenGL|direct'

I get:
direct rendering: No
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2
OpenGL extensions:


While I have an ATI Radeon 9800XT and I want to enable my direct rendering and install the correct ATI driver that allows me to use the compiz-fusion eye candy.

And what do I need for compiz-fusion? A user told me that I need AIXGL while the general HOWTOs say that i need XGL. 

Any advice? and thanks in advance.

---

### Post by wheredidrealitygo on 2007-09-17
I have the 9800 XT as well on a server (sitting beside my desktop), and the driver linked [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") gave me direct rendering, but no compiz fusion.

to install the driver, I did it the bash way (download the file, cd into that directory with a terminal, and then ```
sudo bash ati*.run
```. i chose the direct install option, not generating a .deb.

restart x, and I had my direct rendering.

I then installed compiz fusion (properly, as I have it running on this desktop no problem), and it wouldn't work, whenever I did ```
metacity --replace
``` it would blink like normal, but then not go into compiz, it would just stay in metacity, with an error message that I can track down later, but I remember it saying AIGLX had to be installed, something along those lines.

---

### Post by WolfLust on 2007-09-19
So any advice? I want compiz-fusion to work on my ATI.

---

### Post by WolfLust on 2007-09-19
I installed the restricted driver (using Envy) and now direct rendering works. thanks.

I still need to find an updated compiz-fusion topic that's suitable for ATI

---

