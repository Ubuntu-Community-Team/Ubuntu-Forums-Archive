---
title: "Dragging to select text - im too fast for gnome"
date: 2007-05-29
forum: Desktop Environments
---

### Post by bluedalmatian on 2007-05-29
This is a problem that I've only experienced in Ubuntu, never in Fedora, using the same mouse. If I drag to select a load of text in a program, I have to run the mouse quite slowly. If I go at the speed I normally would the highlighting breaks, at a certain point, and it carries on selecting from there on.

Ive fiddled with the Mouse preferences especially the 3 under the motion tab but it makes no difference.

anyone else experience this or know what causes it ?

thanks
andrew

---

### Post by tgm4883 on 2007-05-29
do you have 3d enabled.  Whats the output of "glxinfo | grep direct"

---

### Post by bluedalmatian on 2007-05-30
no 3d in fact its a rather old machine output of above command is

direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by tgm4883 on 2007-05-30
This might sound weird, but you need to install the drivers for your video card.  The drivers you're using are the "safe" drivers.  Even when I have those drivers installed it's choppy when I scroll down a webpage, and that was on my Athlon XP 2000+

---

### Post by bluedalmatian on 2007-05-31
How can I find out what alternative drivers there are for it (NVidia Riva 128). The Device Manager only seems to list the hardware not say what driver is installed for it.?

---

### Post by tgm4883 on 2007-05-31
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

The nvidia legacy driver should be in the repo

---

