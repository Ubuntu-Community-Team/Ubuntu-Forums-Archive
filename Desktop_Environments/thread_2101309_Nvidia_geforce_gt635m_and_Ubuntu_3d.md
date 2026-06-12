---
title: "Nvidia geforce gt635m and Ubuntu 3d"
date: 2013-01-04
forum: Desktop Environments
---

### Post by erik1001 on 2013-01-04
Hello. Is it possible to enable 3d effects like wobbly windows etc on my GPU?
```
user@pc:~$ sudo  /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
OpenGL version string:  3.0 Mesa 9.1-devel

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

```
```
user@pc:~$ sudo lshw -c video
[sudo] password for user: 
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:3000(size=128) memory:d3000000-d307ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:d3400000-d37fffff memory:e0000000-efffffff ioport:4000(size=64)

```
I have installed nvidia drivers and bumblebee, but running:
```
user@pc:~$ optirun /usr/lib/nux/unity_support_test -p
[ 1838.812264] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[ 1838.812296] [ERROR]Aborting because fallback start is disabled.

```
So is it possible to have some eyecandy on my Ubuntu 12.10 64bit?

---

### Post by erik1001 on 2013-01-08
No one answered on this thread, so I'll update with some more info.
I finally made my bumblebee to work, but now I get:
```
test@test:~$ optirun /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 635M/PCIe/SSE2
OpenGL version string:  4.2.0 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```Should I forget about Unity 3d and all the eyecandy?

---

### Post by jamesensor on 2013-01-25
Hey bro, we're screwed with this videocard. I've tried with bumblebee too but I'm always with the intel gfx. Also, some games in wine are all screwed even if I play them with the optirun cmd.

I really wish they could do something about this type of cards. I love ubuntu but I'm out until there's something reliable and easy to install (proprietary drivers in ubuntu repository, perhaps?). When will it be out?

Regards


If only we could just be with the nvidia card working and leave out the intel hd one.

---

### Post by erik1001 on 2013-01-25
Thank you for your post. 
Yeah, that's exactly what I mean, I use my PC mostly at home with plugged in power supply. It'll be great to have the option on your login screen to choose "Unity with external GPU" and "Unity power saving mode" or something similar. I guess other eyecandy rich DEs are not fully supported on Optimus GPU too?

---

### Post by jamesensor on 2013-01-25
> **erik1001 said:**
> "Unity with external GUI" and "Unity power saving mode" or something similar.

That would be perfect. If unplugged, logout/login. I too use the laptop more often at home. The 3d desktop seems to work (in 12.04), I haven't tried wobbly windows but it's important to have the nvidia card on because of other stuff. I use virtualbox a lot and I think it makes quite a difference. Not to go over the rendering stuff on games again, but ubuntu is on steam and that's important...

Cheers

---

### Post by sunriders on 2013-05-23
hello, i didn't want to create a new thread so i post here:

i installed ubuntu 13.04. installation completes fine, everything appears to work on intel hd 4000 exept brightness, but nevermind. i can't do anything about nvidia 635m. i read so much stuff, i tried different ways to install it, but the result is always the same - blank desktop with mouse cursor. when i try to uninstall nvidia - i cant. terminal says "nvidia driver location not found" or something similar and i have to reinstall ubuntu. i'm tired of trying to make the nvidia card work, tired of unsuccsesful atempts and tired of reinstalling the system. 

is there a way to make it work? or should i stop trying, because it's impossible?

---

