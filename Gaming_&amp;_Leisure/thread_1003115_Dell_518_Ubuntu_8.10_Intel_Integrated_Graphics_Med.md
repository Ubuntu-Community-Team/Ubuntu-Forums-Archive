---
title: "Dell 518 Ubuntu 8.10 Intel Integrated Graphics Media Accelerator X3100"
date: 2008-12-05
forum: Gaming &amp; Leisure
---

### Post by oceanfirehawk on 2008-12-05
Hello everyone,

Games such as Alien Arena, Tremulous, etc. are choppy on my dell 518 with Intel Integrated Graphics Media Accelerator X3100. I am running 8.10 with 2GB RAM? Any help?

---

### Post by hikaricore on 2008-12-05
Intel integrated chipsets are very poor in hardware quality and driver support.
After checking that direct rendering is working properly: 

> glxinfo | grep rendering

Try lowering your video settings in such games including resolution and detail.
If this doesn't work you may want to consider getting a real video card such as an NVIDIA.

---

### Post by eragon100 on 2008-12-06
> **hikaricore said:**
> Intel integrated chipsets are very poor in hardware quality and driver support.
After checking that direct rendering is working properly: 



Try lowering your video settings in such games including resolution and detail.
If this doesn't work you may want to consider getting a real video card such as an NVIDIA.

 Tremulous should run nice on that chipset, but alien arena is a more demanding game. Maybe it will work tough on low settings :wink:

---

### Post by oceanfirehawk on 2008-12-06
> **eragon100 said:**
> Tremulous should run nice on that chipset, but alien arena is a more demanding game. Maybe it will work tough on low settings :wink:

Thanks...but how do I lower the settings. Would I be able to do that outside of the game menu. The reason being that I cannot really make out the game menu. It is choppy.

Thanks,
Jake

---

### Post by oceanfirehawk on 2008-12-06
UPDATE: I installed Fedora 10 and the X3100 works fine. It's still a bit slow in Alien Arena though.

---

### Post by oceanfirehawk on 2008-12-10
Please see the picture attached that I took running Ubuntu. For some reason, the picture includes some of the desktop. The screenshot was taken when I was running Alien Arena at full-screen.

Thanks,
Jake

---

### Post by Sockerdrickan on 2008-12-10
Do you X3100 guys get OpenGL 2.0+ support? :) with shaders

---

### Post by oceanfirehawk on 2008-12-10
> **Tux0r said:**
> Do you X3100 guys get OpenGL 2.0+ support? :) with shaders

I'm sorry, but I don't understand your question.

---

### Post by Sockerdrickan on 2008-12-11
tip: You don't have to answer then. ;)

---

### Post by oceanfirehawk on 2008-12-18
UPDATE: I installed 8.04 on my Dell 518 system and installed Tremulous. It works perfect. I wonder why 8.10 won't work with my X3100.

---

### Post by Orfintain on 2009-12-24
I have the same card and am trying to run Regnum apparently dell ships out bunk video cards with laptops wtf

---

