---
title: "Shadow under top bar turn black"
date: 2011-04-30
forum: Desktop Environments
---

### Post by scyleung on 2011-04-30
The shadow that is meant to appear under the bar at the top of the screen in unity seem to be overlaying on top of itself every time and eventually turned black

here is a picture showing what I mean:
[IMG]http://i.imgur.com/734g1.png[/IMG]

---

### Post by Krytarik on 2011-04-30
If there are similar shadows under usual windows, check the settings in "CompizConfig Settings Manager -> Window Decoration".

Hope it helps!

EDIT: Ah, forget about it, it seems to be a graphical glitch, similar to another one I just yet saw.
Please give some details about your video card/chip and driver.

---

### Post by scyleung on 2011-04-30
> **Krytarik said:**
> If there are similar shadows under usual windows, check the settings in "CompizConfig Settings Manager -> Window Decoration".

Hope it helps!

EDIT: Ah, forget about it, it seems to be a graphical glitch, similar to another one I just yet saw.
Please give some details about your video card/chip and driver.


I am running it on Virtual Box on a Mac
NVIDIA GeForce GT 120 - 128Mb graphical memory set on VM, 3D acceleration on, and the Virtual Box Guest drivers

---

### Post by Krytarik on 2011-04-30
Although I'm not too much into Virtual Box, I noticed that there may be issues with Unity in it, because it heavily relies on 3D-acceleration and proper video support.

But you can allways install Unity 2D, it looks the same as the usual Unity, but, of course, without desktop effects:
```
sudo apt-get install unity-2d
```

---

