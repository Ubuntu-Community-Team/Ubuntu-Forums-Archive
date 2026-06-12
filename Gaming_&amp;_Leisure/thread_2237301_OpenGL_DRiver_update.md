---
title: "OpenGL DRiver update?"
date: 2014-08-01
forum: Gaming &amp; Leisure
---

### Post by karlowbrian on 2014-08-01
Hello, 
When I try to play the game "No More Room in Hell" Steam gives me back an error saying that either my video card is not supported or that Open GL needs to be updated. Now my computer is dual booted with Windows XP and I can run the game just fine on that partition so I know that my video card is supported. So my question is, how do update or install a driver for Open GL?  

System Specs:
Sony Viao VGC RA820G
Pentium 4 3.2 gthz processor (Hyper threaded)
1.5 gb of RAM
Graphics: Gallium 0.4 on ATI RV370
200 GB Hard Drive 
Ubuntu 14.04

---

### Post by karlowbrian on 2014-08-01
Also, I would like to mention that, Gallium 0.4 on ATI RV370, is a Radeon X300 graphics card.

---

### Post by oldrocker99 on 2014-08-01
The fault is most likely the ATI drivers. Some Linux Steam ATI users have had better luck with the open-cource "radeon" driver than with the closed-source ATI fglrx drivers.

---

### Post by karlowbrian on 2014-08-01
Okay, thank you! Am I able to get the open-sourced driver off the ATI website?

---

### Post by Kirk Schnable on 2014-08-01
> **karlowbrian said:**
> Okay, thank you! Am I able to get the open-sourced driver off the ATI website?You might find this documentation page helpful:  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by karlowbrian on 2014-08-01
Thanks Kirk! Helped a lot!

---

### Post by Peter_Solver on 2014-08-02
Have you updated or installed a driver for OpenGL? How did it go? Have you tried running your games again with no issues?

---

### Post by oldrocker99 on 2014-08-03
Also, for gaming, you might want to install a lighter-weight desktop than Unity. Lubuntu-desktop is pretty light,and popular, but I prefer MATE (in the 14.04 repositories; look for mate-desktop), which I have found to be comparable to LXDE in lightweightness, and either is great for gaming.

---

