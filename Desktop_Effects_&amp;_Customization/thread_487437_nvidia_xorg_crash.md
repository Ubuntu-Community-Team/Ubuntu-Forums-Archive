---
title: "nvidia xorg crash"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by mouseboyx on 2007-06-29
If i enable the nvidia driver in the restricted drivers then xserver crashes but luckily i made a backup of my xorg.conf and made a script to replace it fast so i need to know how to keep xorg from crashing with nvidia i have a Nvidia 6200 Turbo Cache

Edit: 
it says that the kernel is version 1.0-9755 but the module for x is 1.0-9631

---

### Post by mouseboyx on 2007-06-29
problem solved: 
sudo apt-get install nvidia-glx-new
nvidia-settings
CTRL-ALT-BACKSPACE
and it worked perfectly i guess i needed the glx-new drivers instead of the plain glx.

---

### Post by alshurooqi on 2007-07-02
I have the same problem and my card nvidia 7100 gs
haw to get the best driver I need to teach 1440*900 for my al1916w screen. I'm only 1024*768

---

