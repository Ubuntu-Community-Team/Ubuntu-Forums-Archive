---
title: "Intel Driver Sandybridge 3D/OpenGL problem"
date: 2012-09-03
forum: Desktop Environments
---

### Post by AnDrummer on 2012-09-03
Hi!
I've a problem in my Samsung notebook with Sandybridge i5 2410m and Intel HD3000 graphic card, on Ubuntu 12.04.
Yesterday I installed an upgrade, with a a new xorg video intel driver.
Now I can't use unity 3D but only unity 2D because I think mesa driver doesn't work properly. Seems to be an OpenGL problem cause I did this test:

**glxgears:**

[B]libGL error: failed to load driver: i965
libGL error: Try again with LIBGL_DEBUG=verbose for more details.[/B]
3906 frames in 5.0 seconds = 781.087 FPS
3913 frames in 5.0 seconds = 782.531 FPS
3906 frames in 5.0 seconds = 781.103 FPS
3902 frames in 5.0 seconds = 780.250 FPS

It runs, but with a 100% cpu usage :(

Now i have the intel driver 2.20.6.
I tried to install an old driver but nothing :(

Thank you

---

### Post by goaliedude3919 on 2012-09-03
Try downloading the Bumblebee drivers: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by AnDrummer on 2012-09-03
Maybe i solve my problem, upgrading drivers xorg and intel from Oibaf PPA :)
I'll test my system tomorrow :)

---

