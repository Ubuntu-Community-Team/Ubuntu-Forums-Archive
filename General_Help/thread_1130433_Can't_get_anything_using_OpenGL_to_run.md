---
title: "Can't get anything using OpenGL to run"
date: 2009-04-19
forum: General Help
---

### Post by bbi5291 on 2009-04-19
I'm running Intrepid Ibex and I have an old nVidia Vanta/Vanta LT video card. According to the release notes, the legacy driver for such cards (package nvidia-glx-71) is not compatible with the version of X.org that comes with this version of Ubuntu. Instead, I installed the nv drivers.

However, I began having problems when I started trying to learn how to use OpenGL. Running OpenGL on X is completely dependent on GLX, isn't it (that would certainly explain the name)? And I tried SDL too, but I guess that's only a layer over OpenGL anyway, so it doesn't work either.

Is the issue with glx fixed in Jaunty, or do I have to...
* downgrade Ubuntu
* buy a new video card
* go back to using Windows
?

---

### Post by cinematography on 2009-04-19
> **bbi5291 said:**
> I'm running Intrepid Ibex and I have an old nVidia Vanta/Vanta LT video card. According to the release notes, the legacy driver for such cards (package nvidia-glx-71) is not compatible with the version of X.org that comes with this version of Ubuntu. Instead, I installed the nv drivers.

However, I began having problems when I started trying to learn how to use OpenGL. Running OpenGL on X is completely dependent on GLX, isn't it (that would certainly explain the name)? And I tried SDL too, but I guess that's only a layer over OpenGL anyway, so it doesn't work either.

Is the issue with glx fixed in Jaunty, or do I have to...
* downgrade Ubuntu
* buy a new video card
* go back to using Windows
?
You should probably just get a new video card since you'll likely have to get one eventually.

---

### Post by CatKiller on 2009-04-19
I don't think the nv driver does accelerated 3D, only 2D. There is the nouveau driver that I believe is attempting to get accelerated 3D working on NVidia cards, but I have no idea what progress they've made.

Having said that, I had also read about NVidia's lack of support for old cards and when my drummer, who has a now-unsupported card, upgraded to Intrepid a couple of weeks ago I thought he'd have to either change video card or use the nv driver, but the driver listed in Hardware Drivers was there and worked perfectly. Perhaps you'll be lucky too.

---

### Post by bbi5291 on 2009-04-19
> **CatKiller said:**
> but the driver listed in Hardware Drivers was there and worked perfectly. Perhaps you'll be lucky too.

What do you mean, driver listed in Hardware Drivers? When I go to Hardware Drivers both boxes are blank and it says "No proprietary drivers are in use on this system."

---

### Post by CatKiller on 2009-04-20
> **bbi5291 said:**
> What do you mean, driver listed in Hardware Drivers? When I go to Hardware Drivers both boxes are blank and it says "No proprietary drivers are in use on this system."

Ah, then you weren't as lucky. He was using a GeForce 2 GTS, I think, and although his card was listed as no longer supported he still had an entry in there that he could use.

---

