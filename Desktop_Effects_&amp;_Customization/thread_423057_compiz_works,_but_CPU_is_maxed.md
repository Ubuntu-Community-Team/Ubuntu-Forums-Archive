---
title: "compiz works, but CPU is maxed"
date: 2007-04-25
forum: Desktop Effects &amp; Customization
---

### Post by jerich007 on 2007-04-25
I have compiz & Feisty working on my T43 laptop w/ATI M300 card.  I had assumed the GPU would offload 3D effects, but when I use the water effects, my CPU gets pegged at 100%.  glxinfo shows I have 'Direct rendering' enabled.  Am I missing something?

- Jericho

---

### Post by mrpaco on 2007-04-26
Is your CPU load only at 100% when water is enabled?  I am not too familiar with the internals of the M300, but it is possible that it lacks the ability to do the water effects in hardware, causing your CPU to have to render the water effect (OpenGL requires that any rendering features that cannot be performed by the hardware be performed by software rendering)

---

### Post by jerich007 on 2007-04-26
Seems like the CPU spikes whenever I do anything effects-related, like rotating the cube or showing all windows by putting the mouse pointer in the corner.  It's only really noticeable when I use the water effect (shift-F9), then after my screen is filled with drops and ripples it takes a long time to turn off the effect.

---

