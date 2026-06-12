---
title: "[SOLVED] GLX problem: Xserver loads libglx.so without error, then unloads it"
date: 2008-12-03
forum: Desktop Environments
---

### Post by Cracauer on 2008-12-03
I can't figure it out.

This is xorg git version, all installed into an alternate path. Things work fine and I have direct rendering.

But it does not load GLX.
```

(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in th\
e config file.
(II) "dri" will be loaded. This was enabled by default and also specified in th\
e config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dri"
(II) Loading /opt/cvsversions/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.99.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /opt/cvsversions/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.99.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) UnloadModule: "glx"
(II) Unloading /opt/cvsversions/lib/xorg/modules/extensions//libglx.so
(EE) Failed to load module "glx" (no error, 0)

```

As you can see in the lines concerning libglx.so and libdri.so, both are treated precisely the same way, there are no errors and no warnings.

Except that it decides to unload libglx.so for no apparent reason.

The result is a X11 server with direct rendering and all, but lacking GLX nobody can use it :)

Any idea what's going on here?

Will append full log.

---

### Post by Cracauer on 2008-12-03
Figures. I fiddle with it for days. After I post the next git update to devhead fixes it.

Please mark fixed. It was a simple bug in xfree. For those facing the same issue, the part that needed updating from git is "xorg-server".

---

### Post by Izek on 2008-12-03
> **Cracauer said:**
> Please mark fixed.

Thread tools (at the top of the thread) and choose mark as solved.

---

