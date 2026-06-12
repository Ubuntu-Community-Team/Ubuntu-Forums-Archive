---
title: "Unity 3D refusal - FGLRX workaround?"
date: 2011-05-01
forum: Desktop Environments
---

### Post by waspbloke on 2011-05-01
I have a (recent) Dell Studio XPS laptop and running the unity test reveals:
```
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3670
OpenGL version string:  1.4 (2.1 (3.3.10665 Compatibility Profile Context))

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```

Either my graphics card is missing the GL vertex buffer object feature or I suspect the FGLRX driver is to blame.

I am running with the "ATI/AMD proprietary FGLRX graphics driver".

The Q&A on this wiki page: [https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements) - says "We have had some issues with the fglrx driver but we have been able to resolve them. With the fglrx driver, you will be missing features such as Kernel Mode Setting (KMS)."

So can anybody shed any light on how I might me able to resolve my issues? Or at least be able to know for sure whether it is my hardware or the driver that is lacking?

On a side rant, I think ubuntu has dropped the ball a bit here. "Unity" is a misnomer and "Duality" would be more appropriate as previously, pretty much any machine I installed ubuntu on would display the same 'unified' desktop environment. Now however, we have this division imposed upon us with a haves and have-nots desktop discrimination.

---

### Post by waspbloke on 2011-05-01
So I got rid of the ATI/AMD proprietary FGLRX driver and replaced it with XOrg radeon driver. Now unity checks OK and loads but I'm left with a mess of artifacts and trails that only go away after maximizing a window.

So my graphics card works and as I suspected the FGLRX driver seems to be the problem. Maybe ATI/AMD will update it soon and all will be well but for now I don't see how the wiki claim that they have resolved issues with Unity and FGLRX driver stands up.

---

