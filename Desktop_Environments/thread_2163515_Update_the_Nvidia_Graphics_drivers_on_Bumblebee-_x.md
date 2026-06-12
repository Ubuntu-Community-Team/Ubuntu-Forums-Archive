---
title: "Update the Nvidia Graphics drivers on Bumblebee- xorg uses the nvidia drivers"
date: 2013-07-18
forum: Desktop Environments
---

### Post by sireangelus on 2013-07-18
Xorg tries to load the glx driver!!! help..

laptop: i3 3110m
          8gb ddr3

          nv620m

Bumbleebee works fine, but if i try to install a more updated version of the nvidia drivers it breaks the intel drivers and xorg is not accelerated nor i can use compositing or anything that bases on glx without using optirun! how can i fix this? Be advised: i don't have a main xorg.conf.

xorg.0.log: [http://pastebin.com/RGTJSspW](http://pastebin.com/RGTJSspW)

---

### Post by dino99 on 2013-07-19
if you expect usefull help, then provide the required details:
- which laptop model ?
- which graphic drivers version tested ?

---

### Post by sireangelus on 2013-07-19
xubuntu 13.04 x64

ppa bumblebee stable

i3-3110
8gb of ram
NVidia 620m (drivers described as " 304-308")


I am also unable to compile any version of the NVidia driver on any kernel higher than 3.9.6(using the same .config!)

---

### Post by grahammechanical on 2013-07-20
We can only have one video driver activated at a time. Bumblebee is an open source driver. If you then install a Nvidia driver then Bumblebee will be deactivated. You do not tell us but because you speak of Bumblebee we can assume that you have Nvidia Optimus technology.

Nvidia has only just started developing a Linux driver for its Optimus technology. It could be that the Nvidia driver you are installing is not capable of running this hybrid video set up.

The Bumble bee project was started as a response to Nvidia's failure to provide a suitable driver in the first place. Owners of Nvidia Optimus technology are much better served now than when Optimus first came out.

This link shows just how far behind Nvidia is in serving its Linux customers.

[http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/nvidia-releases-linux-graphics-drivers.html)

You may be getting better service from Bumblebee.

Regards.

---

### Post by sireangelus on 2013-08-01
ok... so, i'd like to update the nvidia driver  i use WITH bumblebee and not being stuck with the 304.308 default one.

---

### Post by sireangelus on 2013-08-20
Up...

---

### Post by sireangelus on 2013-08-27
Upppppp

---

