---
title: "Desktop effects could not be enabled with nvidia 256 driver"
date: 2010-06-09
forum: Desktop Environments
---

### Post by lordbah on 2010-06-09
Can't get compiz working. In gnome-appearance-properties every attempt to set any visual effects gives a busy dialog "Searching for device drivers" for a minute, then some screen blinking, and finally "Desktop effects could not be enabled". Console output says:

(gnome-appearance-properties:11165): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.

(gnome-appearance-properties:11165): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

(gnome-appearance-properties:11165): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:11165): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

-- that message appears many more times --

Ubuntu 10.04. Nvidia 8300 GS.

Previously, I had compiz working, using the nvidia 195 driver downloaded from the nvidia site and installed by "sudo sh NVIDIA-Linux-x86-195.36.24-pkg1.run". This worked great locally but not through VNC ([https://bugs.launchpad.net/xorg-server/+bug/353126](https://bugs.launchpad.net/xorg-server/+bug/353126)). A fix for that bug became available for Lucid, version 256 of the binary nvidia drivers, packaged at [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates).

I ran "sudo sh NVIDIA-Linux-x86-195.36.24-pkg1.run --uninstall" to remove that version. Used Synaptic to remove anything nvidia related. Then used it to install the new version.

"modprobe nvidia" would complain that it couldn't find any such driver. More research lead me to copy /usr/lib/nvidia-current/modprobe.conf to /etc/modprobe.conf.d - it contains "alias nvidia nvidia-current". Now "modprobe nvidia" no longer complains.

Hardware Drivers (jockey) said the driver was activated but not currently in use. More research finally showed me that I need to reinstall nvidia-common. Now jockey was happy but things still didn't work. I deactivated and reactivated the new driver, didn't change anything.

After more searching, and translating a page from Russian, I wiped out xorg.conf and ran "nvidia-xconfig -render-extension -render-accel -composite -damage-events -add-argb-glx-visuals" and rebooted. Still no help.

NVIDIA X Server Settings, on the OpenGL/GLX Information tab, says "Failed to query the GLX server vendor".

I'm not sure whether or not glxinfo is relevant, but it also says "Error: couldn't find RGB GLX visual or fbconfig".

I reinstalled "libgl" and "mesa" packages via Synaptic.

I disabled metacity compositing.

compiz-check finds some problems. I don't know what they mean.

To me, the Xorg.0.log and dmesg look fine. I've visited hundreds of web pages, finding people with the same symptoms, with dozens of different solutions, but none have worked for me. (Part of that problem is of course that a lot of the solutions were for much olders versions of Ubuntu or different variants, or for different graphics cards). I don't know where to go from here. It seems like the immediate problem is that the root visual is not a "GL visual" in spite of the fact that xorg.conf says AddARGBGLXVisuals (I don't actually know the meaning of those terms however).

I've probably left out lots of stuff.

---

### Post by lordbah on 2010-06-10
The compiz-check is a shell script which is calling glxinfo, so no surprise that it reports failures given that glxinfo isn't working.

"strace glxinfo" shows it opening /usr/lib/libGL.so.1, which is a symlink to libGL.so.1.2, which is dated 2009-10-13 and 403 KB. Shouldn't it be using /usr/lib/nvidia-current/libGL.so.1, which is a symlink to libGL.so.256.29, which is dated 2010-05-30 and 765 KB? Did some step get missed during installation? Was there something that I was supposed to do by hand?

---

### Post by lordbah on 2010-06-10
Found I had to remove both /usr/lib/libGL.so.1 and /usr/lib/libGL.so.1.2. If I only removed the first, then any run of ldconfig resurrected the link. Also I couldn't find any package to remove which would remove both of those files. So I removed them manually, ran ldconfig, and now glxinfo works and I can enable desktop effects.

I don't know whether or not this will survive any kind of upgrade though.

---

### Post by Frogs Hair on 2010-06-10
Is it important that you run the 256 driver ? It is a beta driver and they have issues at times .

---

### Post by lordbah on 2010-06-10
"Important", perhaps not, but I did want to verify that it fixes an issue with VNC. It does.

---

