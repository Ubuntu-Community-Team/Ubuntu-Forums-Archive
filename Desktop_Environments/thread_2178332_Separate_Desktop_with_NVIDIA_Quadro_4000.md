---
title: "Separate Desktop with NVIDIA Quadro 4000"
date: 2013-10-03
forum: Desktop Environments
---

### Post by nanisahu on 2013-10-03
Hi,
Please suggest me how to configure the **separate desktop with NVIDIA Quadro 4000 2x** (GPU 0 & GPU 1) in **Ubuntu 12.04 LTS** (3.2.0-52 generic kernel version).
I tried the following method.
  1. In NVIDIA settings ,X Server Display Configuration -> Configuration
          a.Disabled
          b.**Separate X screen(requires X restart)**
          c.TwinView
      I selected the option **"b"** for separate Desktop, but the second display (GPU 1) has no desktop but it filled with** white screen**, **mouse cursor** display is like **X mark** and **keyboard input was not taking**.
In **Xinerama the extended display** has the **Unity Launcher** also extended to second display(GPU 1), but extended display means the GUP 0 has to extended to GPU 1.

 **But in 10.04 LTS (2.6.32 kernel) it was working fine with same NVIDIA Quadro 4000 for separate desktop in this version.**

I want to make **three separate desktop with two GPU's. **(Like three different machine has the different desktop)

Thank you,
Nani Sahu

---

