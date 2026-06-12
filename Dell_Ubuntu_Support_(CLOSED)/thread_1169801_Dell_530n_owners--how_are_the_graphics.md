---
title: "Dell 530n owners--how are the graphics?"
date: 2009-05-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MattPhillips on 2009-05-25
Hello,

I'm considering getting the 530n with pre-installed Ubuntu (and 4GB RAM).  However like previous offerings it comes with the integrated GMA 3100 gfx card, which looks generally weaker than current basic nVidia/ATI offerings.  So I'm wondering how people are finding the graphics on this system.  I have some specific questions too, based on previous experience with Dell/Ubuntu:

1. What is the output of 

$ glxinfo | grep direct

Is it direct rendering: No or direct rendering: Yes?

2. Anything weird when you run 

$ glxgears 

(especially if direct rendering *is* enabled)?  Does the client area of the window float on top of other windows, if you e.g. drag the glxgears frame across a internet browser page?

3, Can you install your own graphics card if you want to?

Thank you!

Matt

---

### Post by floborg on 2009-05-25
I have been running Compiz fine since I got the system last October.  That was with Hardy.  I'm now using Jaunty and it feels the same.

Direct rendering is enabled.  Nothing strange happens in glxgears.

I should say that I had to disable Compiz and crank down the video settings quite a bit when I tried Nexius.

I assume I am using X3100 graphics, since that's what was advertised by Dell.

lspci yields

```
VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
```

lshw yields

```
 *-display UNCLAIMED
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
```

---

### Post by MattPhillips on 2009-05-25
Thank you!

---

### Post by MattPhillips on 2009-05-25
Hello,

I think what I'd really like to know is whether or not the 530n under Ubuntu fully supports the OpenGL capabilities of the GMA 3100 graphics card, which according to wikipedia is 1.5 or greater?  Anybody come up against any opengl rendering that should work, but doesn't?

Thanks,
Matt

---

