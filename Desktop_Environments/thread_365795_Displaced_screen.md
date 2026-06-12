---
title: "Displaced screen"
date: 2007-02-20
forum: Desktop Environments
---

### Post by JuliusC on 2007-02-20
Hello, So I'm not sure if I post this here or in Multimedia forum... but this is my question:
I'm using two PCs, both running with Ubuntu 6.06, one has GeForce 6600 working fine with the binary driver (thanks tseliot), the other one uses the i810 for intel integrated graphics card. I use just one LDC 17" monitor (acer) across a KVM. The problem comes when I switch between the Ubuntu desktops; because the screen appears displaced 1 cm aprox, I adjust the image in the monitor but when I switch back to the other Ubuntu desktop it is displaced 1 cm in the other hand. 
This only occurs with the Ubuntu desktops because if I boot the windows partition that I have in one of them I can swith between Ubuntu desktop and windows desktop without adjust the image in the monitor (if it is previously adjusted in Ubuntu).
If anyone has seen a similar problem or has a possible solution I would appreciate it very much!

---

### Post by orb9220 on 2007-02-20
If you leave ati alone and adjust it. Then in nvidia-settings there is x server display configuration which shows position. example mine shows absolute +0+0.

Maybe adjusting those zero values might help. Be sure to save to x config file button after changing.

---

