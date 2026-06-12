---
title: "Video Resolution 3D effects Compaq dx6100MT"
date: 2008-02-29
forum: Desktop Environments
---

### Post by dodgeyrog on 2008-02-29
I have installed Ubuntu on a Compaq dx6100MT Mini Tower PC - it works a treat and I got Compiz Fusion running with a 3d spinning cube and everything I rebooted it today and resolution is rubbish and cannot get desktop effects to start.

My question - how do I check the video card and set resolution properly?

It is currently picking up Vesa Generic Vesa card?

The chipset is either Intel/Nvida or ATI 

thanks for any pointers.

Rog

---

### Post by overdrank on 2008-03-02
> **dodgeyrog said:**
> I have installed Ubuntu on a Compaq dx6100MT Mini Tower PC - it works a treat and I got Compiz Fusion running with a 3d spinning cube and everything I rebooted it today and resolution is rubbish and cannot get desktop effects to start.

My question - how do I check the video card and set resolution properly?

It is currently picking up Vesa Generic Vesa card?

The chipset is either Intel/Nvida or ATI 

thanks for any pointers.

Rog

HI and welcome, please post the output of the command ```
lspci
``` 
In the terminal located under applications, accessories, terminal and look for VGA and this will identify your hardware.

---

### Post by EXCiD3 on 2008-03-02
Use the restricted drivers manager to install you graphics drivers located in System menu.

---

### Post by dodgeyrog on 2008-03-04
Output from lspci

noc@noc-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
40:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
noc@noc-desktop:~$ 


Thanks

---

