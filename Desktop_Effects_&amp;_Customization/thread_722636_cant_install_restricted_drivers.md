---
title: "cant install restricted drivers"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by rude_lee on 2008-03-12
when  i go to restricted drivers to install my onboard graphics it says "Your hardware does not need any restricted drivers." and i cant use compiz how do i check my graphics and enable 3d rendering and such

---

### Post by overdrank on 2008-03-12
> **rude_lee said:**
> when  i go to restricted drivers to install my onboard graphics it says "Your hardware does not need any restricted drivers." and i cant use compiz how do i check my graphics and enable 3d rendering and such

Hi and what is the model of the graphics card? You can use the command lspci and look for VGA to identify the graphics.

---

### Post by rude_lee on 2008-03-17
this is thw lspci output

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by rude_lee on 2008-03-17
yeah sis mirage graphics is wat it is

---

### Post by Ub1476 on 2008-03-17
Make sure the correct driver is set in System>Administration>Screens and graphics. Remember to test the driver before you apply it!

---

### Post by overdrank on 2008-03-17
> **rude_lee said:**
> yeah sis mirage graphics is wat it is

Hi and you may find some help here
[http://ubuntuforums.org/showthread.php?t=450176](http://ubuntuforums.org/showthread.php?t=450176)

---

### Post by uberlube on 2008-03-17
Dont rely on activating your graphics card in the RDM. Use ENVY to install your drivers and they will work fine.

---

### Post by Ub1476 on 2008-03-17
> **uberlube said:**
> Dont rely on activating your graphics card in the RDM. Use ENVY to install your drivers and they will work fine.

He doesn't use an ATI nor nvidia card. Therefore, it's probably just the wrong driver set in* Screens and graphics*.

But yes, Envy is great otherwise.

---

### Post by uberlube on 2008-03-17
My bad. Didn't read thoroughly enough.

---

