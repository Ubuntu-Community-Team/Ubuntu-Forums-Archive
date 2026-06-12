---
title: "Picture Colors Different From Windows - Profile Issue ?"
date: 2009-03-10
forum: General Help
---

### Post by ubuwatson on 2009-03-10
I am a very satisfied user of Ubuntu and I am currently using 8.10.  One thing that I use my laptop for more than anything else is image processing.  I have noticed that when I view an image in Ubuntu regardless of the application, the colors and contrast are off.  If I compare the same images side-by-side with other machines running windows xp/vista (or when I dual boot into Windows on the same machine), the images have a bit more snap (more contrast, more saturated color and more dynamic range - whites seem to clip).

I noticed that ubuntu is showing my card at a 24 bit color depth compared to windows which shows 32 (though I am uncertain if this difference would really impact anything or not).  The graphics card is fully capable, a GeForce 8400 (GO) 256 M Ram.

The graphics driver itself seems to be working well, the system is snappy and of course the compiz effects are fluid.  The colors in the OS itself look fine, blacks are pure black and whites and pure white, so I am puzzled to say the least.

Any thoughts ?

---

### Post by prince_niceguy on 2009-03-10
24 bit is same as 32 bit in windows, read some where about it. the color issue may be related to the settings in your graphics driver. if it is nvidia try playing around with the properties to see if it is resolved.

---

### Post by ubuwatson on 2009-03-10
> **prince_niceguy said:**
> 24 bit is same as 32 bit in windows, read some where about it. the color issue may be related to the settings in your graphics driver. if it is nvidia try playing around with the properties to see if it is resolved.

Thanks - Good to know about the 24b vs 32bit, I kinda figured as much as my display doesn't show any signs of banding.

I did mess around with the gamma curves in the Nvidia X-Server configuration.  Is there any way to use an ICC Color Profile ?

---

### Post by prince_niceguy on 2009-03-10
I do not use nvidia but have seen my friend tweak using sliders somewhere in nvidia x server config application.

---

