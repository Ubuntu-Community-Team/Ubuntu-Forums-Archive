---
title: "Slow performance of the User Interface with 8.10"
date: 2009-01-25
forum: General Help
---

### Post by OmarHawk on 2009-01-25
Hello,

yesterday I installed XUbuntu on my PC with an integrated GPU
(nVidia GeForce 8200 mGPU).

The installation of the nVidia binary drivers worked fine. OpenGL seems to work using the drivers (glxinfo & glxgears report the vendor string "NVIDIA", glxgears reports 1400fps).

However the user interface "feels" terribly slow. You can watch the screen darken when entering the super user password or when logging out.

Scrolling down a Google search in FireFox slows down to a crawl!

As I have used FireFox under Linux before, I KNOW it can be A LOT faster. The nVidia driver displays the usage of the "nVidia 2D acceleration technology" in the X servers log file.

Did i miss anything during the installation?

Thanx,
Carsten

---

### Post by taurus on 2009-01-25
Which version of nvidia driver did you install from System -> Administration -> Hardware Drivers?

---

### Post by HunterK on 2009-01-25
I can say from experience on my nvidia 6800GT... even with the 177 drivers, the whole interface just seemed slow and clunky.  I upgraded to 180.18 (180.22 dont work for me for some reason) and everything is smooth as silk.  Huge improvement.  

I think nvidia made some updates that fix some X compatibility issues.

---

### Post by OmarHawk on 2009-01-25
> **taurus said:**
> Which version of nvidia driver did you install from System -> Administration -> Hardware Drivers?

I am using nvidia-glx-177.

---

### Post by adamlau on 2009-01-25
Then give nvidia-glx-180 a shot. Another way to improve the overall response of Firefox is to compile an optimized PGO build.

---

### Post by OmarHawk on 2009-01-31
Hello,

after trying nvidia-glx-180 the UI is indeed A LOT faster.

Thanx for the suggestion!

---

