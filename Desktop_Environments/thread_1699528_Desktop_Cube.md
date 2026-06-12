---
title: "Desktop Cube"
date: 2011-03-03
forum: Desktop Environments
---

### Post by TimmZerp on 2011-03-03
How do I create the desktop cube? I tried enabling normal and extra visual effects, but it says they cannot be enabled.

---

### Post by overdrank on 2011-03-03
> **TimmZerp said:**
> How do I create the desktop cube? I tried enabling normal and extra visual effects, but it says they cannot be enabled.

Hi and welcome, you may need to install the graphics driver. You can start at system, administration, hardware drivers to see if any are available for your system.
You can identify your graphics card with the command 
```
lspci | grep VGA
``` in the terminal. The terminal is located under applications, accessories. Then copy and paste the command and the output.

---

### Post by TimmZerp on 2011-03-03
It says there aren't any drivers available and when i put in the code i got back this: 00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
...I'm not exactly sure what any of that means. I am running Ubuntu on a virtual machine, could that have something to do with it?

---

### Post by deconstrained on 2011-03-04
I found the posts here to be somewhat informative:
[http://forums.virtualbox.org/viewtopic.php?f=1&t=16](http://forums.virtualbox.org/viewtopic.php?f=1&t=16)
Long story short it would seem that a virtual graphics adapter cannot interface with the graphics adapter on the host that's running the virtual machine in a way that could take advantage of its 3D acceleration/rendering capabilities.

Also, while it may be irrelevant: hardware acceleration in a virtual environment seems a bit like an oxymoron, to me at least.

UPDATE: The aforementioned thread is pretty old. This is newer:
[http://www.dedoimedo.com/computers/virtualization-3d-support-vmgl.html](http://www.dedoimedo.com/computers/virtualization-3d-support-vmgl.html)
It looks promising, albeit difficult.

---

