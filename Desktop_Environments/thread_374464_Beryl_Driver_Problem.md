---
title: "Beryl Driver Problem"
date: 2007-03-02
forum: Desktop Environments
---

### Post by nerds in parties on 2007-03-02
Hello again. I've installed the Ubuntu Ultimate Edition that already has Beryl installed. the problem is that it just does not work. maybe it has to do with the driver I installed for my ATI Mobility Radeon X1600 (the edgy eft)

when I type "Beryl" at the terminal I get this: 

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by Waappu on 2007-03-02
Hi

If you use "fglrx" driver you need use XGL. "fglrx" driver not support composition.
I thing open suorce driver isn't support your card
[https://help.ubuntu.com/community/RadeonDriver#head-b60183e198b030e0c2d76385685c6073aec882af](https://help.ubuntu.com/community/RadeonDriver#head-b60183e198b030e0c2d76385685c6073aec882af)

---

