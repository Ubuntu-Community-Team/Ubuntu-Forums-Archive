---
title: "Video card drivers."
date: 2005-12-14
forum: General Help
---

### Post by erhard on 2005-12-14
Hey guys. I finally installed Ubuntu on my old box aswell, the only problem is the graphics card in the box is an onboard one. The exact name of the card is "Sis 661FX" and i wanted to know where to find drivers for it.

Thanks is advance,
Erhard

---

### Post by erhard on 2005-12-14
Anyone? :(

---

### Post by erhard on 2005-12-14
Anyone?:(

---

### Post by Perfect Storm on 2005-12-14
Is it 2D or 3D card? I have never heard of it. Who made it?

Can you see it in the **Device Manager**?
**System** ---> **Adminstration** ---> **Device Manager**

---

### Post by cjazz on 2005-12-14
What happens if you type

sudo dpkg-reconfigure xserver-xorg

and select "sis" from the list of drivers? According to the wiki at [http://wiki.x.org/wiki/VideoDrivers](http://wiki.x.org/wiki/VideoDrivers), your card is supported under the sis driver. I don't know how Ubuntu's implementation might affect that or if that means full 3d acceleration or not.

---

