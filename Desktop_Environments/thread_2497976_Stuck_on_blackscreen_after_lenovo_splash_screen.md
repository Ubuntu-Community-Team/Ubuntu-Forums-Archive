---
title: "Stuck on blackscreen after lenovo splash screen"
date: 2024-05-24
forum: Desktop Environments
---

### Post by mooncake-98 on 2024-05-24
I'm sorry if this a dumb question but I don't know where to look and I am new to ubuntu

I wanted to try out kde plasma on my freshly installed ubuntu (24.04)  machine, install went as described but after the restart I can only get  past the lenovo splash screen. anyone know what I can do to fix this?

I specifically tried to install kde with 
sudo apt install kde-standard

the device I am using is lenovo ideapad slim 5 16irl8

---

### Post by currentshaft on 2024-05-24
Try logging in to serial console with Control+Alt+F1 through F7

---

### Post by MAFoElffen on 2024-05-25
Does your Lenovo have nVidia graphics? Have you tried using "nomodeset" as a boot parameter temporarily to use safe graphics mode until you install your graphics drivers?

---

