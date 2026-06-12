---
title: "Beryl no XGL pb"
date: 2006-09-30
forum: Desktop Environments
---

### Post by FuzZy2006 on 2006-09-30
I've just installed beryl following the instructions. I've used compiz before so I didn't have to install XGL. The problem I have is that when i try to run beryl in the terminal it says: ```
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension

```. If I try to use the beryl manager and switch to the beryl windows manager, it tries to do this but it fails, returning to metacity. ](*,) 
Pls help

---

### Post by FuzZy2006 on 2006-09-30
i've unchecked launch-fall back window .... and i can check beryl but nothing happens, nothing changes

---

### Post by ss0007 on 2006-10-01
> **FuzZy2006 said:**
> i've unchecked launch-fall back window .... and i can check beryl but nothing happens, nothing changes

Does anybody know the solution for the above issue ?
I am in the same situation now .... 

PLs help

---

### Post by infol on 2006-10-01
Have you created an Xgl session for gdm (or xdm, or whatever you are using) and a startup script for Xgl?

---

### Post by ss0007 on 2006-10-01
> **infol said:**
> Have you created an Xgl session for gdm (or xdm, or whatever you are using) and a startup script for Xgl?

I think i have, but how do i know which xserver (xgl or X) is currently running ?

Thanks

---

### Post by ss0007 on 2006-10-01
the problem is now solved .. my second reboot made me to start the beryl somehow ...

---

### Post by FuzZy2006 on 2006-10-09
i updated to edgy eft and then i followed a guide and installed nvidia beta drivers and beryl. :D

---

