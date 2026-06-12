---
title: "Compiz doesn't work - software rendering enabled?"
date: 2011-02-09
forum: Desktop Environments
---

### Post by AegisXLII on 2011-02-09
Hello all,

I know this is a common issue, but I've looked all around and troubleshooted this for days with no luck.

I recently re-installed Ubuntu 10.10 on my laptop. Upon attempting to enable compiz, it would not work. I received the standard error - "software rasterizer in use."

> compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

Here's the compiz-check output:

> Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G86M [Quadro NVS 135M] (rev a1)
 Driver in use:         nouveau
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 


I spent a long time messing around with drivers before settling on the nVidia binaries recommended by Ubuntu which are supposed to support hardware acceleration as per:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

(At least I think I did. The directions say that they will install the nvidia binaries, yet when I go to System > Administration > Additional Drivers, it says that no proprietary drivers are in use)

But no luck. Compiz-check output is the same, and glxinfo | grep render still yields:


> :~/Desktop$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Software Rasterizer
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_fragment_program, 


If you know what else I should try, I'd like to hear about it! Thanks in advance.

---

### Post by Forlong on 2011-02-10
The nouveau driver in Maverick is not able to run Compiz. You'll need to install the proprietary nvidia driver.

Try running
```
gksu software-properties-gtk
```
and enable **maverick-proposed** in the **Updates** tab.

After you have updated the software sources, see if there's a driver in **System &#8594; Administration &#8594; Additional Drivers** available

---

