---
title: "Dell E6420 video problem."
date: 2012-11-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kova78 on 2012-11-01
Hello everybody.

I want to explain what happened to my laptop Dell e6420 with Ubuntu 32bit 12.04 (3.2.0.32 kernel).

Last week my laptop frozen in two different days without any type of error and it was been necessary  to reboot through the power-on button.
Ok, I thought that there were some problems with the new kernel and the video drivers.
It's ok, go ahead.
I did a backup with Remastersys (god bless the authors) and when I reboot the laptop, unity worked at 2D mode.

```
echo $DESKTOP_SESSION
ubuntu-2d
``````
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.4

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
```What???
I thought that It was a problem with virtualbox (VMWARE), no way....I purge it, I followed all guides to re-install mesa, intel and any type of proprietary drivers (nvidia included)...but at the end there was not been a solution to return back to unity 3D!!!
In the purge and reinstall steps, something went wrong and my ubuntu is died :-(

Well, I decided to re-install it with the remastersys backup. At the boot I noticed that also the live-cd runned to 2D (so it was an old problem, before the backup).
I installed the backup and in the update manager I selected the precise-proposed updates.
In the repository there was the 3.2.0.33 version of the kernel, I installed and unity has returned back to 3D :D :D

```
echo $DESKTOP_SESSION
ubuntu
``````
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
OpenGL version string:  3.0 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```Great!!! But It has worked for only 3 days until the compat wireless driver installation.
In fact, this morning I installed the driver for the first time, I uninstalled them and finally I re-installed them....at the second reboot, unity has returned to work in 2D mode!!!

At the end...I reinstalled (for the second time) the remastersys backup.

What does it happened?
How can I solve this problem for the next times?
Now I am scared to install and do anything!!

Thank you very much for the help!

Have a nice day!
Bye.

---

### Post by viluski on 2012-11-06
Hi!

I got exactly the same problem of unity working in 2D after installing a 2012-10-30 release of compat-wireless. My computer is a Dell Inspiron 14z. Apparently it's quite a new problem having issues with video after installing compat-wireless since I couldn't find anything really from the forums.

---

### Post by uclugLee on 2012-11-06
Dell E6400, E6410 and E6420

I duplicated the issue on all three laptops.

Not sure if it's a bug, but I submitted a report anyway.

---

