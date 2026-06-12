---
title: "How can I fix it? Graphic screen did no display after instalation of ubuntu!"
date: 2006-06-02
forum: Desktop Environments
---

### Post by sidy on 2006-06-02
Hi there,

My PC:
AMD 64 processor.
1G Ram.
Motherboar: Asus K8V-X.
Graphic Card: nVidia Corporation NV34 [GeForce FX5200LP].
Ubuntu installed: 5.10 64bit.

I had this problem before (graphic screen no displaying), and I fixed dooing this:

Ctrl+alt+F1
sudo dpkg-reconfigure xserver-xorg
nv
nv nVidia FX5200LP
#enter in all the rest, then#
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm restart

Then graphic screen displayed, but at this time it didn't.](*,) 
So, WHAT CAN I DO TO HAVE GRAPHIC SCREEN DISPLAING?
Or, WHAT HAVE I DONE WRONG AT THIS TIME?
Or, WHAT SOULD I DO DIFFENT TO FIX IT?

I'm not an expert, can you please give me same directions, step by step, please!

Rgds.

---

### Post by SqRt7744 on 2006-06-02
[QUOTE=sidy]
So, WHAT CAN I DO TO HAVE GRAPHIC SCREEN DISPLAING?
Or, WHAT HAVE I DONE WRONG AT THIS TIME?
Or, WHAT SOULD I DO DIFFENT TO FIX IT?

I'm not an expert, can you please give me same directions, step by step, please!

Rgds.[/QUOTE]

I have more or less the the same chip in my laptop and find that nv has difficulties with it.  It will work if you choose the 'vesa' driver instead of 'nv'.  Vesa is quite slugish though, so at your earliest convenience install nvidia-glx.

# sudo apt-get install nvidia-glx
# sudo nvidia-glx-config enable

---

