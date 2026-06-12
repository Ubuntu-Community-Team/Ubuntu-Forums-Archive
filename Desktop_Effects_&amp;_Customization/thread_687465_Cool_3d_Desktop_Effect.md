---
title: "Cool 3d Desktop Effect"
date: 2008-02-04
forum: Desktop Effects &amp; Customization
---

### Post by tom_the_drummer on 2008-02-04
Hi guys,

looked on youtube and there are some people who are doing cool things with the multiple desktops - namely spinning them round - they are on a cube.

How can I do this?

I think you need something called compiz which I have downloaded but can't work out how to install!


Thanks for all the help guys


Tom

---

### Post by blazercist on 2008-02-04
what video card do you have and which version of ubuntu are you running?

---

### Post by Cew27 on 2008-02-04
set the cube up in compiz and press control + alt and click and drag

---

### Post by tom_the_drummer on 2008-02-04
> **blazercist said:**
> what video card do you have and which version of ubuntu are you running?

The latest version of ubutnu and its the one in my laptop - not sure what it is! 64MB intel chipset one I believe.

---

### Post by edm1 on 2008-02-04
> **tom_the_drummer said:**
> The latest version of ubutnu and its the one in my laptop - not sure what it is! 64MB intel chipset one I believe.

open the terminal, type 'lspci' and post the output here so we can see what make/model your card is.

---

### Post by kryth on 2008-02-04
you should be able to get compiz config system manager (aka ccsm) on sympatec .... it will show up in 
system>prefferences> Advanced desktop effects after installing.

---

### Post by blazercist on 2008-02-04
lspci | grep VGA 
that should tell us your video card.... If its intel you should just be able to 
sudo apt-get install compiz
compiz --replace

and thats it.

---

### Post by tom_the_drummer on 2008-02-04
tom@LAPTOP:~$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

Thats the info!

---

### Post by bogdan_5844 on 2008-02-04
do this:

open Synaptic (System->Administration->Synaptic Package Manager),search for ccsm,right click it and select Mark for install.Apply the changes,then close Synaptic.

Then go to System->Preferences->Appearance.Select the Visual Effects tab,make sure Custom Settings is checked.If not,check it.

After that,open System->Preferences->Advanced Desktop Effects Settings,and check these effects: 

Desktop Cube
Rotate Cube 

After that,click Rotate Cube,and change the Zoom parameter to 0.600.
You're done.To try the cube out,press Ctrl and Alt,then move the mouse pressing left click to see the cube

---

### Post by tom_the_drummer on 2008-02-04
CCSM is not found in the synaptic manager when I do a search fo it.

Tom

---

### Post by FuturePilot on 2008-02-04
Make sure all the repositories are enabled in System&#8594;Administration&#8594;Software Sources.

---

### Post by bogdan_5844 on 2008-02-04
no,my mistake

the package name is compizconfig-settings-manager not ccsm

my bad :lolflag:

---

