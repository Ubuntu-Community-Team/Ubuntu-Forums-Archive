---
title: "small problems Dell XPS 1330"
date: 2008-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Binford8000 on 2008-10-14
Hello,

I bought the notebook with preinstalled Ubuntu and noticed, that it used a special kernel received via a special repository ([https://launchpad.net/~dell-team/+archive](https://launchpad.net/~dell-team/+archive)).
But I killed the installation because I wanted 64bit and complete hard drive encryption. Unfortunately I did not run intensive test with that special kernel.
Let's look at my problems:
 - Memory Sticks Pro are not recognized in the card reader (I heard there is no kernel driver available for **internal** card readers)
 - The Numpad does not generate numbers when it's activated, still numbers. And yes, "control the mouse with the numpad" is deactivated

I hope you can help me to solve these problems and/or to analyze what's different with the dell-kernel.

---

### Post by Binford8000 on 2008-10-15
ok I fixed the numpad with a BIOS switch - my fault.
But the Memory Sticks? seems like I have to wait until a kernel driver is supported. The Dell repository contains only a special kernel module package with updated intel wimax drivers.

---

