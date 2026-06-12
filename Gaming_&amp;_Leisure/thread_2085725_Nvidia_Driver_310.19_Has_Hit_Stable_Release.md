---
title: "Nvidia Driver 310.19 Has Hit Stable Release"
date: 2012-11-18
forum: Gaming &amp; Leisure
---

### Post by Dlambert on 2012-11-18
I really wish I could get email updates about these drivers, but here's the changelog:

> 
[LIST]
[*]Added support for OpenGL 4.3.
[*]Added  a new X configuration option, "UseHotplugEvents", to allow the  suppression of RandR events when adding or removing non-DisplayPort  displays. See the "X Config Options" appendix of the README for details.
[*]Added support for configuring stereo in nvidia-settings when stereo is enabled in the X configuration file.
[*]Added support for configuring the ViewPortIn and ViewPortOut for display devices in nvidia-settings.
[*]Fixed  metamode bookkeeping when modifying the display configuration in the "X  Server Display Configuration" page of nvidia-settings.
[*]Added support for configuring rotation and reflection per display device in nvidia-settings.
[*]Implemented  workarounds for two Adobe Flash bugs by applying libvdpau commit  ca9e637c61e80145f0625a590c91429db67d0a40 to the version of libvdpau  shipped with the NVIDIA driver.
[*]Fixed an issue which affected the performance of moving windows of VDPAU applications when run in some composite managers.
[*]Added unofficial GLX protocol support (i.e., for GLX indirect rendering) for the GL_ARB_pixel_buffer_object OpenGL extension.
[*]Added  support for HDMI 3D Stereo with Quadro Kepler and later GPUs. See the  documentation for the "Stereo" X configuration option in the README for  details.
[*]Added experimental support for OpenGL threaded  optimizations, available through the __GL_THREADED_OPTIMIZATIONS  environment variable. For more information, please refer to the  "Threaded Optimizations" section in chapter "Specifying OpenGL  Environment Variable Settings" of the README.
[*]Improved performance and responsiveness of windowed OpenGL applications running inside a Unity session.
[/LIST]
                                                                         [http://www.geforce.com](http://www.geforce.com)

How to install: 

[http://ubuntugaming.blogspot.com/2012/11/how-to-install-nvidia-drivers-in-ubuntu_9.html](http://ubuntugaming.blogspot.com/2012/11/how-to-install-nvidia-drivers-in-ubuntu_9.html)[]("http://www.gamingonubuntu.blogspot.com")

---

### Post by flowerdealer on 2012-11-22
Does anyone know if this are going to be released as experimental in the 12.10 repositories?

---

### Post by TesX on 2012-11-23
> **flowerdealer said:**
> Does anyone know if this are going to be released as experimental in the 12.10 repositories?

I hope so!
No matter if there is in experimental or in nvidia-current-updates, they have to be released in the official repos!!!

This, according to me, it's a moment that is a trampoline for Linux  for games and maybe even for apps.
If we don't make updated drivers available as soon as they're released (or with a few days of delay) or if we don't make the support available, how can we hope that Linux will be succesfull?

I think Canonical should put all the effort it has in this moment...
If they work hard and succeed, it will be a very positive advertisement for Linux in general.

Who knows... we may even see Photoshop on Linux soon!!! :popcorn:

PS: Sorry if I mistyped something, English is not my main language...

---

