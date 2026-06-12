---
title: "No direct rendering fglrx with glx enabled"
date: 2007-12-28
forum: Desktop Environments
---

### Post by Slipie on 2007-12-28
Hi everybody,

I've been searching the internet for an answer for quite some time now but can't find the solution for my problem :(
I have an ATI X700 videocard in my laptop and running Gutsy on it.
2weeks ago I read that ati finally got xgl support build into their driver so I decided to replace the opensource driver with the one from ati.
compiz-fusion and all work very well indeed and when I run glxgears I get higher fps than ever.
But now I want to try running games with the new driver and that's where my problem starts.
Direct rendering is a no.
And I got the very common error running glxinfo:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
libGL error: XF86DRIQueryDirectRenderingCapable failed
```

My X log has got the following entry:

```
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
```

So it looks like it's enabled.
When I do fglrxinfo I get:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.0.6473 (8.37.6)
```

As you can see the screens differ from each other between the glxinfo and fglrxinfo command.
Now I don't know much about that stuff but it doesn't look right to me.
When I start a GNOME session without glx enabled, direct rendering is enabled and the screen is on 0.0 when I run glxinfo.

Does anyone know how I can fix this?

Regards,
Robbert

---

### Post by Forlong on 2007-12-28
You are using the fgrlx driver from the repos - this one does not work with AIGLX but only with Xgl.
If you want to use the latest driver from ATI you have to install it manually - that one has support for AIGLX (not Xgl - that's the "workaround" that always worked).
But I don't recommend that. It's still buggy with Compiz/AIGLX.

If you're able use Compiz atm, you must have Xgl installed - then the DRI issue is normal.

I advise you go back to the open radeon driver, if it worked for you before (that's what I use too).

In case you don't know how to do that, don't hesitate to ask.

---

### Post by Slipie on 2007-12-30
Hmmm, well that's too bad.
I will have to wait for the stable driver from ATI with AIGLX support.
I think I will stay on this driver because it's much faster (like 90%) than the radeon driver.
Thanks Forlong!

---

