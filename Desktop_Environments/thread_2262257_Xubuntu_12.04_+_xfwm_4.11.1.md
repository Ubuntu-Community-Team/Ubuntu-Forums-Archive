---
title: "Xubuntu 12.04 + xfwm 4.11.1"
date: 2015-01-23
forum: Desktop Environments
---

### Post by 3246251196 on 2015-01-23
I always stick with LTS. I upgraded XFWM 4; the main reason being because it enables me to tile windows to the side of the screen.

Anyway, I have now noticed on two machines runnung 12.04 and 4.11.1 that every time I reboot if I have an image selected as my desktop background and it is smaller than the entire screen then the "Solid Color" reverts back to Red (this is the background of the screen outside the limits of the centred image): this is not what I want. What I want is for it to stay as I selected which is black.

Anyway to solve this?

Cheers.

---

### Post by 3246251196 on 2015-01-25
In a bid to try and understand what was happening I download the source for xfdesktop4 to see if there were any defaulted colors there. Anyway I realised that after compiling it and make install it seems to have corrected itself. Perhaps I needed to "refresh" some configuration files after upgrading xfwm4.

---

