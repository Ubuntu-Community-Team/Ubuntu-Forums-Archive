---
title: "Kube desktop"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by Kube2007 on 2008-01-09
Hi there, im new the world of Linux but i am very impressed so far, the thing is is that i've seen a picture of a screen where there is a kube on the desktop & each side is a seperate window that can be rotated and selected, does any body know what i mean? Could somebody please tell me how to do this please?

Thanks!:confused:

---

### Post by luisromangz on 2008-01-09
You have to enable Copiz, having a compatible video card, for example Nvidia or ATI (with the latest drivers from the ATI website, not the ones from the ubuntu repositories)

---

### Post by Kube2007 on 2008-01-09
Thanks for the swift reply, could you tell me how i would enable compiz please & what i should do next? I'm a complete beginner when it comes to Linux:lolflag:

---

### Post by some-guy on 2008-01-09
First, check what kind of graphic card you have, if it's an Intel one it should work right away in gutsy, if it's nvidia go to System > Administration > Restricted Drivers and get the driver afterward open a terminal and type ```
sudo nvidia-xconfig --add-argb-glx-visuals
sudo nvidia-xconfig -d 24
```
and it'll work, if it's ATi go to System > Administration> Restricted Drivers and get it, after that install xserver-xgl :grin:

---

### Post by Kube2007 on 2008-01-09
I have a nvidia graphics card, when i type a command in Terminal and press enter it wont let me type in a password:confused:

---

### Post by jryprt on 2008-01-09
> **Kube2007 said:**
> I have a nvidia graphics card, when i type a command in Terminal and press enter it wont let me type in a password:confused:

The password dos not show up into terminal but it really is typing it after you type it hit enter.

---

### Post by chris4585 on 2008-01-09
[http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200]("http://howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-nvidia-geforce-fx-5200")

tutorial on how to enable compiz very nice

---

### Post by jryprt on 2008-01-09
[This](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#) is a good guide after the 1 up 1 post.

---

