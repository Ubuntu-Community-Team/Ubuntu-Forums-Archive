---
title: "Just installed Ubuntu, Steam missing lib"
date: 2015-06-09
forum: Gaming &amp; Leisure
---

### Post by laydralae on 2015-06-09
I just installed Ubuntu 14.04 last night and after getting the wireless to work I am now having difficulty getting steam to run. I'm new to Linux but I've tried various solutions found on the internet to try and get steam to install. Each solution seems to get me one step closer, but the problem persist. I downloaded Steam from the Ubuntu Software Center and after running the installer Terminal gives me this:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.4)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 

After which I get a prompt giving me:
> You are missing the following 32-bit libraries, and Steam may not run:
libGL.so.1

After which Steam tries to run and then hits me with a fatal error prompt:
> Fatal Error: Failed to load steamui.os

About my hardware
I am duel booting Ubuntu on a MacBook Pro 13inch 2012 model using 7.7 GiB of memory, using a Intel Core i7-3720QM CPU @ 2.60GHz x8 processor, and a Gallium 0.4 on NVE7 graphics card. Yes, this is a x64 OS.

Help would be most appriciated.

---

### Post by MikeCyber on 2015-06-10
Looks like you need to install your graphics driver with synaptic. Or maybe the 32bit libs, google should help you with that.

---

### Post by TechTorpedo.com on 2015-06-11
you can try the following commands:

install ia32-libs from synaptic or sudo apt-get install ia32-libs
in Terminal: sudo sh -c 'echo "/usr/lib32\n/usr/lib/i386-linux-gnu/mesa\n" >> /etc/ld.so.conf.d/steam.conf' && sudo ldconfig

---

### Post by R33D3M33R on 2015-06-12
Try to run ```
sudo apt-get install -f
```

---

