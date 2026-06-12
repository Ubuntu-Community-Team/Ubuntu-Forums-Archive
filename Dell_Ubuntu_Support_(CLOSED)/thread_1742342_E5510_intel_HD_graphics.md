---
title: "E5510 intel HD graphics"
date: 2011-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by memsb on 2011-04-28
I'm running in I7 620M with intel Hd graphics. I've recently upgraded to 11.04 as i wished to try out unity and i was hoping that the graphics problems i was having on maverick would go away. However unity won't run due to lack of 3d acceleration due to the drivers being hopeless.

lspci gives:
```
VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

I've tried adding the PPA's:

[http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu)
[http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu)

and updating, but there is no change.

I could understand there being some issues when maverick came out as the chipset was fairly new. But i tried everything i could find and waited patiently for 6 months hoping for a solution, but now i am at a loss.

Any help will be gratefully received!

---

### Post by memsb on 2011-04-29
I find it hard to believe that i'm the only person to have this problem, or that there is no solution. Am i posting int he wrong section perhaps?

```
glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 

```

---

