---
title: "Ati radeon x300 no Opengl,effects..."
date: 2010-03-03
forum: Desktop Environments
---

### Post by andreselsuave on 2010-03-03
Hi there, I have an ati radeon x300 (RV370). It is supposed to be compatible with 3d effects through the open source driver, but composition doesnt work neither in gnome (compiz) or kde (kwin). Starcraft doesnt work either. Everything used to work with my previous card: Nvidia 3700GT (I think) and had to replace it because it wasn't working properly. I already uninstalled all the nvidia-related software. I never installed the propietary ati driver, since it's not compatible with my card.

Anyone knows what's happening? 

andreselsuave

---

### Post by tgalati4 on 2010-03-03
With the open ati driver, what is the output of:

glxinfo

What are some of the errors in /var/log/Xorg.0.log?

cat /var/log/Xorg.0.log

---

### Post by andreselsuave on 2010-03-04
Thx for the speed answer :P

I changed to a nvidia video card and installed the latest drivers. However, Im curious about the ati error... I may install the ati card on monday and try again. I will tell you then. Thx a lot

---

### Post by tgalati4 on 2010-03-04
That is one way to solve an ATI graphics driver problem--install nVidia.

---

