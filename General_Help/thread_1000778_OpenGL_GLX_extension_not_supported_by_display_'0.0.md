---
title: "OpenGL GLX extension not supported by display ':0.0'"
date: 2008-12-03
forum: General Help
---

### Post by Anicka on 2008-12-03
Hallo everyone!

Since Friday I am having a strange problem with my beloved Ubuntu 8.04. At about lunch time there was a number of updates available (new nvidia-driver and kernel 2.6.24-22). Anyway after this update I noticed that every time I tried to start a program that I use for work I would get this error message:
```
freeglut (/path/to/program): OpenGL GLX extension not supported by display ':0.0'
```
I have tried to load into an old kernel, downgrade the nvidia-glx-new, reinstall freeglut3 and the program I want to use and all of its dependencies. No luck...

When I run glxgears, I get
```
glxgears 
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

I have done some googling saying edit the loaded modules in xorg.conf, but without success.

This is from the Xorg.0.log, the rest can be found in the attachment:
```
grep -i glx /var/log/Xorg.0.log
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

Does anyone out there have a solution to this?

---

### Post by Anicka on 2008-12-12
](*,)

---

### Post by tuxp3 on 2008-12-12
My first thoughts:
1. Boot into new kernel (no X, just CLI -- kill X/gdm or use single-user mode)
2. Uninstall all nvidia packages
3. rmmod all nvidia modules (I think its just 'nvidia')
4. lsmod | grep -i 'nvidia' to be sure
5. reinstall nvidia packages
6. play with update-alternatives to select the nvidia-glx
7. modprobe nvidia (and any other related modules, if any)
8. restart X/gdm

I know you tried downgrading/reinstalling kernel/nvidia but I don't know what order you did that in, so It might be worth your time to try it again in this order.

Good Luck
(also double check /etc/X11/xorg.conf to be sure that the nvidia driver is being selected)

---

### Post by Anicka on 2008-12-12
Thank you for your fast answer.

Actually I don't use the nvidia-drivers at all. My ubuntu is the guest in a vmware workstation. It's just that a program I use has decided to be depending on the nvidia-glx-new package being installed.

I only know that it was working and suddenly wasn't and in between there were a few packages being upgraded. Trying to revert/purge and reinstall didn't help. So here I am.

I will try to play a little bit more with my installation. Since the program that I cannot use now is the main reason for my running ubuntu in the first place, I have little to loose.

But maybe this is a hint, I have a broken sym-link /usr/lib/nvidia/libGL.so.1.xlibmesa -> libGL.so.1.2
Could that be a problem?

---

