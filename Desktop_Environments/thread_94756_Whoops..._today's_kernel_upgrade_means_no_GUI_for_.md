---
title: "Whoops... today's kernel upgrade means no GUI for older nvidia cards"
date: 2005-11-24
forum: Desktop Environments
---

### Post by jonny on 2005-11-24
Today's kernel upgrade broke X on my system.  For some reason, Update Manager updated the kernel to 2.6.12.10 but failed to also update nvidia-legacy to the same version.

If anyone else out there has the same problem, you need to reboot your machine using the old kernel (you'll have this option on the Grub menu that appears if you press escape when you first turn on your PC), open Synaptic Package Manager and install the nvidia-legacy package version that matches your new kernel.  I needed the linux-restricted-modules-2.6.12-10-k7-nvidia-legacy package; you need to match the k7 part to the type of kernel you have installed.   If you don't know what that means or if you haven't changed the default kernel, you need to install the linux-restricted-modules-2.6.12-10-386-nvidia-legacy package.

---

### Post by rejser on 2005-11-24
which cards are affected? Are we talking gf4mx or tnt cards?

---

### Post by orbinick on 2005-11-24
[quote=rejser]which cards are affected? Are we talking gf4mx or tnt cards?[/quote] 
i guess thats the case because with newer cards, (I think geforce 2 and up) you DO NOT need nvidia-legacy packages.

---

### Post by jonny on 2005-11-25
It affects anyone using the nvidia-legacy package.  I think that it's generally for anything earlier than a GeForce 4, but there are a few exceptions.

---

### Post by teaker1s on 2005-11-25
appears my 
NVIDIA Corporation NV17 [GeForce4 MX 440]
is now a legacy driver requiring both nvidia legacy glx and the restricted module for the kernel wasn't installed since this kernel update and interestingly my ubuntu/kubuntu system showed ubuntu loading I now have Kubuntu blue splash screen

---

