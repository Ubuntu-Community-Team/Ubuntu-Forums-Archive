---
title: "Using a Projector - Keystone Correction"
date: 2019-02-08
forum: Gaming &amp; Leisure
---

### Post by Drowz0r on 2019-02-08
Hello all

I'm new to using a projector but we want to fix one to the ceiling. I'm told, and looking it up online, that keystone correction may be needed, depending on the keystone correction the projector is able to produce.

Does anyone know of any keystone projection software that is available for Ubuntu, or if there is a native feature that I'm missing?

Thanks

---

### Post by TheFu on 2019-02-08
Keystone correct is part of every projector that I've seen.  Use the remote that came with the projector to set it up and forgetaboutit.  It isn't something handled by **any** source of video.

---

### Post by Drowz0r on 2019-02-09
I've definitely seen windows software out there do it - just wondered if there was a known Linux one.

There is a keystone correction built in but it's often only around 15 degrees.

---

### Post by TheFu on 2019-02-09
> **Drowz0r said:**
> I've definitely seen windows software out there do it - just wondered if there was a known Linux one.

There is a keystone correction built in but it's often only around 15 degrees.

Google found this [https://lists.freedesktop.org/archives/xorg/2013-October/056056.html](https://lists.freedesktop.org/archives/xorg/2013-October/056056.html) - looks like X11 can be used for it. I've never tried.  For screen resolution changes, I generally use lxrandr, but it can only enable/disable monitors and alter resolutions. The xrandr manpage has examples for setting up keystone correction. There is a "See Also" mention of xkeystone, but no manpage for it and the program doesn't run for me - it uses an interpreter that I've never heard about, nickle. I installed nickle and xkeystone crashed.  Probably some unhandled dependencies.

Maybe the proprietary GPU driver for your card can do something?
Looks like nvidia abandoned theirs [https://www.nvidia.com/object/feature_nvkeystone.html](https://www.nvidia.com/object/feature_nvkeystone.html)

[https://ubuntuforums.org/showthread.php?t=1282950](https://ubuntuforums.org/showthread.php?t=1282950) is a prior question here, no answer.

Looks like manually using xrandr is the way.;(

---

### Post by Drowz0r on 2019-02-09
Yeah I've definitely made the screen all weird accidentally on my NVIDIA drivers - but I'm not sure which device I'm hooking up to the projector yet (it hasn't even arrived yet, waiting on the post). I imagine it'll be some low tech thing that can just... fire out movies when needed. Maybe even just a tablet or something. I'll need to experiment.

I'll take a sniff at the link. Thanks.

---

