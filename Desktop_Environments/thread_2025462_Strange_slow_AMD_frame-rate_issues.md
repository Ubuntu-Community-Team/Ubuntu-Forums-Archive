---
title: "Strange slow AMD frame-rate issues"
date: 2012-07-14
forum: Desktop Environments
---

### Post by Gannin on 2012-07-14
For specs, I have an AMD FX-4100 with an AMD Radeon HD 6850 graphics card.  I'm using the AMD proprietary drivers.

I'm experiencing some strange framerate slowness in Linux.

Let's start with glxgears.  When I run it, I get 300 fps and the process is pegged at about 100% CPU utilization.  If, in the Catalyst Control Center, I go into 3D > More Settings and turn vertical refresh off, it goes about to around 12,000 and still with 100% CPU.  If I then also disable the tear free setting, it goes up to about 44,000 still with 100% CPU.

Each time, regardless of configuration, it takes my CPU from its lowest speed step (1.4 GHz) to its highest speed step (3.60 GHz) and leaves it there the entire time it's running.

Then I tried Ryzom.  With tear free and 3D vertical refresh both turned on, I get maybe 1 FPS in Ryzom.  With both turned off, I get maybe 3 - 5 FPS in Ryzom.

And with Ryzom, just like with glxgears, regardless of setting, it pegs the CPU at 100% at its full 3.60 GHz speed step.  If I forcibly lower the speed step of my processor and set it to, say, 1.4 GHz or 1.7 GHz, the FPS of the game gets even slower and choppier.

My computers specs are well above the required, and the recommended, for Ryzom.  It doesn't seem it should be pegging my system so hard.  Any thoughts?

Update:

I did some testing with Unreal Tournament 2004, another game my system should barely notice.

With tear free and 3D vertical refresh off, the frame rate is good but the CPU still bumps up from 1.4 GHz to 3.60 every few seconds or so.  It seems to me it shouldn't do that on such an old game.

With tear free enabled, be 3D vertical refresh still disabled, the frame rate is still decent, but the graphics get jumpy.  As in, you move the mouse and the screen moves smoothly for a bit then everything just jumps or skips a few pixels.  In this setting, the CPU gets pegged to max speed more often than with everything off.

With both tear free and 3D vertical refresh on, the frame rate is still okay but the graphics are still jumpy and skippy, and the CPU is pegged at max speed the entire time.

---

