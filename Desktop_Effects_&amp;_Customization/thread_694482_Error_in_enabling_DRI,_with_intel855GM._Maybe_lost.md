---
title: "Error in enabling DRI, with intel855GM. Maybe lost package."
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by ridgemao1983 on 2008-02-12
I can't enable DRI.

When I ran the command of glxinfo, I thought something was wrong in libGL, because it didn't get the correct path for its OpenDriver(i915_dri.so). As a result, I can't turn on my desktop effects. 

My path for the file i915_dri.so is at /usr/lib/dri, and making a link for this path or export  LIBGL_DRIVERS_PATH would cause other problems.

But when I used ubuntu Live CD to start my lap-top, I could turn on my desktop effects. And when I ran the command of glxinfo, I could see that it got the correct path for OpenDriver(i915_dri.so), i.e. /usr/lib/dri.

So I thought it must be the problem of libGL or something like that, maybe it was due to that I had removed or updated some packages. Now I want to undo it, but I don't know what packages are related to libGL.

Any suggestions? Thanks!

PS. 
My video card is the integrated intel 855GM. And the result after running glxinfo is:

ron@ron:~$ glxinfo | grep direct
libGL: XF86DRIGetClientDriverName: 1.8.0 i915 (screen 0)
libGL: OpenDriver: trying /usr/X11R6/lib/modules/dri/i915_dri.so
libGL error: dlopen /usr/X11R6/lib/modules/dri/i915_dri.so failed (/usr/X11R6/lib/modules/dri/i915_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to find driver: i915_dri.so
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

Have installed these package: 
libgl1-mesa-dri, 
libgl1-mesa-glx, 
xserver-xorg-video-intel

These Options in xorg.conf will make my display crash.
VideoRam 65536
Option "NoAccel" "false"
Option "DRI" "true"

---

### Post by ridgemao1983 on 2008-02-12
I got my DRI work now, but I don't think it is a good solution. I enabled the desktop effects and the DRI after doing these modification.

sudo ln -s /usr/lib/libGL.so.1.2 /usr/X11R6/libGL.so
sudo ln -s /usr/lib/libGL.so.1.2 /usr/X11R6/libGL.so.1
sudo rm /usr/X11R6/libGL.so.2
And don't forget to make appropriate backup before modifying these files.

It seems that I should use the libGL file located in the /usr/lib, instead of the original one located in /usr/X11R6/lib. I got the idea by running "ldd /usr/X11R6/bin/glxinfo", both in my installed ubuntu and in the Live CD's ubuntu. And I found the difference was that they used different libGL.so.1 file.

However, I don't think it is a good solution, maybe I still got some problems in 3D that has not appeared yet. I still think this problem is due to inappropriate updating packages,  which resulted in the wrong libGL installed on my lap-top.

The newest libGL must be installed at /usr/X11R6/lib, as said on the official website:
[http://dri.freedesktop.org/wiki/DriTroubleshooting](http://dri.freedesktop.org/wiki/DriTroubleshooting)  ["Userspace Setup" section]

So I think my problem is due to installing the newest package about libGL, I should remove it, but I don't know how to do it.

Any suggestions? Thanks!

---

