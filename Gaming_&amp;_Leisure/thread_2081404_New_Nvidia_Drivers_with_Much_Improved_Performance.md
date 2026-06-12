---
title: "New Nvidia Drivers with Much Improved Performance"
date: 2012-11-06
forum: Gaming &amp; Leisure
---

### Post by Dlambert on 2012-11-06
Details: > The result of almost a year of development by NVIDIA, Valve and other  game developers, the new GeForce R310 drivers are designed to give  GeForce customers the best possible Linux-based [PC gaming]("http://ctt.marketwire.com/?release=950026&id=2242348&type=1&url=http%3a%2f%2fwww.geforce.com%2fgames-applications%2fpc-games%23source%3dpr") experience — and showcase the enormous potential of the world’s biggest open-source operating system.
 Available for download at [www.geforce.com]("http://ctt.marketwire.com/?release=950026&id=2242351&type=1&url=http%3a%2f%2fwww.geforce.com%2fdrivers"),  the new R310 drivers were also thoroughly tested with Steam for Linux,  the extension of Valve’s phenomenally popular Steam gaming platform that  officially opened to gamers starting today.
 “With this release, NVIDIA has managed to increase the overall gaming  performance under Linux,” said Doug Lombardi, vice president of  marketing at Valve. “NVIDIA took an unquestioned leadership position  developing R310 drivers with us and other studios to provide an  absolutely unequalled solution for Linux gamers.”
 The R310 drivers support the newest [GeForce GTX 600 series GPUs]("http://ctt.marketwire.com/?release=950026&id=2242354&type=1&url=http%3a%2f%2fwww.geforce.com%2fhardware%23source%3dpr"),  which have redefined gaming for desktop and notebook PCs by combining  revolutionary performance and gaming technology features with an  incredibly power-efficient design. Gamers with previous generation  GeForce GPUs, including the 8800 GT and above, are encouraged to [download these new drivers]("http://ctt.marketwire.com/?release=950026&id=2242357&type=1&url=http%3a%2f%2fwww.geforce.com%2fdrivers%23source%3dpr") as well.



Source: [http://ubuntuxtreme.com/news/nvidia-304-64-r310-drivers-deliver-massive-performance-boost-to-linux-gaming/](http://ubuntuxtreme.com/news/nvidia-304-64-r310-drivers-deliver-massive-performance-boost-to-linux-gaming/)

ChangeLog: > **Release Highlights**

 									 										 										
[LIST]
[*]Added support for the following GPUs:
[LIST]
[*]VGX K1
[*]VGX K2
[/LIST]
[*]Added a missing 32-bit compatibility library for libnvidia-opencl.so to the 64-bit Linux installer package.
[*]Fixed a regression in backlight control functionality on some notebook configurations.
[*]Fixed a performance issue with recent Linux kernels when allocating and freeing system memory.
[*]Fixed a bug that sometimes prevented the display device / X screen selection menu from being displayed in nvidia-settings.
[*]Fixed a bug that prevented X driver gamma manipulation from working after a VT-switch on some configurations.
[*]Added the option "--output-file" to nvidia-bug-report.sh to allow specifying a custom filename for the log file.
[*]Fixed a hang when using OpenGL programs with some SLI Mosaic configurations on pre-Fermi GPUs.
[*]Added sections to the "Supported NVIDIA GPU Products" list for NVS, Tesla, and VGX products.
[/LIST]
									
 									

---

### Post by R33D3M33R on 2012-11-07
If you will see the [original PR]("http://nvidianews.nvidia.com/Releases/NVIDIA-Delivers-Massive-Performance-Boost-to-Linux-Gaming-8ac.aspx"), you will notice that the doubled performance was achieved **only** for *Left for Dead 2*. So they compared L4D2 Wine performance and the optimized Valve engine performance now.

---

### Post by Dlambert on 2012-11-07
I've experience overall better performance in all my games! :)

---

### Post by JimBuntu on 2012-11-09
Okay guys, how do we activate this new driver. I can't it when I'm in the "additional drivers" tab of "Software Sources". Yes, I checked the box for "proposed". I'm running 12.10 64bit.

---

### Post by Dlambert on 2012-11-09
In order to install these drivers one must download the .run from nvidia's website and follow my guide for the Binary drivers: [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by holastickboy on 2012-11-10
> **Dlambert said:**
> In order to install these drivers one must download the .run from nvidia's website and follow my guide for the Binary drivers: [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

What about the nvidia-experimental 310.14, is that just the beta?  Is the actual 310.14 out?

---

### Post by jerome1232 on 2012-11-10
> **Dlambert said:**
> In order to install these drivers one must download the .run from nvidia's website and follow my guide for the Binary drivers: [http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)


Much easier to use the ppa. [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Dlambert on 2012-11-10
> **holastickboy said:**
> What about the nvidia-experimental 310.14, is that just the beta?  Is the actual 310.14 out?

The most current stable is 304.64. I can't wait for 310, but my guide will work for 3.10Beta.

> **jerome1232 said:**
> Much easier to use the ppa. [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)


I've had the PPA break my system too many times to count. And I live by the saying "If you want something done right, do it yourself" :)

---

