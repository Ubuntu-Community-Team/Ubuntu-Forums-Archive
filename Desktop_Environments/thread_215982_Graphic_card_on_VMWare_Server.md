---
title: "Graphic card on VMWare Server"
date: 2006-07-14
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-14
I have Windows XP Pro installed on through VMWare Server in Ubuntu, but the graphic card that appears it's: VMWare SVGA II

It's possible to configure the real graphic card (I have an ATI Radeon 9500)

---

### Post by slider on 2006-07-14
VMWare creates a virtual machine and maps calls into the virtual machine to the host OS so any hardware specific calls that the ATI driver might make wouldn't work. The only graphics card that XP has access to is the virtual one created by VMWare.

---

