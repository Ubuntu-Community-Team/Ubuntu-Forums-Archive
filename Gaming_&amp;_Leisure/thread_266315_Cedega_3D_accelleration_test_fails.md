---
title: "Cedega 3D accelleration test fails"
date: 2006-09-27
forum: Gaming &amp; Leisure
---

### Post by DSn0wMan on 2006-09-27
Direct Rendering is working with ATI Mobility 300M, but when I run the Cedega test it fails on 3D accelleration.

Using ATI proprietary driver fglrx

Any Ideas why this is failing?

---

### Post by 1oki on 2006-09-27
check this site out...


I dont have ATI on this machine.. Nvidia. But I came acrossed it when I was trying to install my drivers :) hope it is usefull...


[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2)

---

### Post by DSn0wMan on 2006-09-27
That wiki is actually describing exactly how I installed it. I think the probem is something with "dri", but thats just a guess. There really aren't any aparent errors when I run glxinfo.

---

### Post by manzuk on 2006-09-28
A friend of mine has the same problem with an Nvidia2
Although the test says he doesn't have 3dacceleration, games actually work. GLXinfo also states DRI is functional.
But as none uf us is a Linux-guru, we just left it like that :D

---

### Post by 1oki on 2006-09-29
I had that problem too... when i ran the tests it showed the GL gears running fine! But it says the test failed.. go figure... I installed the Nvidia drivers and it works fine now, passes all the tests! :)

---

### Post by DSn0wMan on 2006-09-29
Good News! Upgraded to Edgy Beta! Open source ATI driver works perfectly with my Radeon Mobility 300M. 1500 FPS on glxgears, and all Cedega tests pass.

---

