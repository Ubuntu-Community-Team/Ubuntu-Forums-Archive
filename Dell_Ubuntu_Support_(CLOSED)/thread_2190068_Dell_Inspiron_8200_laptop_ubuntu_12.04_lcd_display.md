---
title: "Dell Inspiron 8200 laptop ubuntu 12.04 lcd display problem"
date: 2013-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ranger12 on 2013-11-25
Hi all, I have installed ubuntu 12.04 lts on a Dell Inspiron 8200 laptop. It has a Nvidia Geforce chip and it will output to an external monitor with no issues but there is no display on the built-in lcd monitor. I tried using the FN-CRT/LCD button on the laptop but that does not work. I know it is not a hardware problem bucause I can boot my eComstation beta demo cd with it and the builtin display works just fine. Anyone have any suggestions? Is there something in grub or X that needs to be changed?

---

### Post by ranger12 on 2014-01-28
Okay I have solved the problem. First, I upgraded to the 12.04.4 release. After that I upgraded to the lts-saucy packages: linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy. The internal display displays everything just fine now.:D I am going to upgraded with these packages on my desktop as well. I also installed the lts-saucy kernel on my server.

---

