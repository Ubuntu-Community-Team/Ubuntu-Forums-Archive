---
title: "NVIDIA xserver resolution issues"
date: 2009-05-22
forum: General Help
---

### Post by cj13579 on 2009-05-22
When I turn on my pc the log on screen doesn't fill the screen. there is a black strip, about an inch wide, on the right hand side. This disappears once I login but the res is really low (800x600). I have to change my nvidia xserver settings every time I login because, for some unknown reason, after i edit my resolution to what I want (1280x1024_70) it wont save my preferences to xorg.conf.

My graphics card is a GeForce 6100 and i'm using NVIDIA 180.44 drivers.

Any help with this would be much appreciated, thanks in advance!

EDIT: My monitor is a Relisys TL966A

---

### Post by Feelin_froggy8877 on 2009-05-29
Not sure about the login screen, but, I have to go through the same thing every reboot, for some reason after installing the nvidia driver xorg's highest res is 800x600, and have to reset res, refresh rate and my twin view. though, you can run "sudo nvidia-settings" from a term and save steings to xorg. I personally am having issues with this and have been fishing for a solution for a while now. Let me know how it works for ya.

---

