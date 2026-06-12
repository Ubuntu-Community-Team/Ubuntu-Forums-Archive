---
title: "Games Not Displaying Properly"
date: 2009-04-08
forum: Gaming &amp; Leisure
---

### Post by rossmc92 on 2009-04-08
I've recently been in the mood for pc gaming but no game whatsoever seems to work. So far I've tried Alien Arena, Wolvenstein: Enemy Territory, Tremulous, and Open Arena. In all of them the mouse eventually turns into a black square, writing disappeared and the screen flickers.In Wolvenstein there was also no sound. Any help would be greatly appreciated.

---

### Post by Chemical Imbalance on 2009-04-08
Can you tell us what card you have or what drivers you are using?

If you do not know your card, post the output of

lspci

in Terminal.

---

### Post by rossmc92 on 2009-04-08
> **Chemical Imbalance said:**
> Can you tell us what card you have or what drivers you are using?

If you do not know your card, post the output of

lspci

in Terminal.

ross@ross-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.1 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
02:06.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
02:06.5 Communication controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Smart Card Controller
02:0e.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
ross@ross-laptop:~$

---

### Post by Chemical Imbalance on 2009-04-08
Okay, so far the prospects aren't looking good.  That intel chipset is not exactly meant for playing 3D games.  I struggle on my Dell's intel gm965 to get playable framerates.  

Honestly, you aren't going to get decent frames on games like Tremulous, etc... with that card.

I know from experience, I own two computers with Intel chipsets and they frankly suck.

Do you have a desktop or a laptop?  And what version of ubuntu do you have?

---

### Post by rossmc92 on 2009-04-08
> **Chemical Imbalance said:**
> Okay, so far the prospects aren't looking good.  That intel chipset is not exactly meant for playing 3D games.  I struggle on my Dell's intel gm965 to get playable framerates.  

Honestly, you aren't going to get decent frames on games like Tremulous, etc... with that card.

I know from experience, I own two computers with Intel chipsets and they frankly suck.

Do you have a desktop or a laptop?  And what version of ubuntu do you have?

Laptop. 8.10 

[http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,39190556,00.htm](http://reviews.zdnet.co.uk/hardware/notebooks/0,1000000333,39190556,00.htm) - just a link to it.

---

### Post by Chemical Imbalance on 2009-04-08
Hmmm, I suggest you try some lower-spec games for that laptop.  That intel chipset can't really handle 3D-intensive games well.  

If you like fps's, this one has slightly lower requirements:

AssaultCube: [http://assault.cubers.net/](http://assault.cubers.net/)


To install, download the linux version from the site.  Then right-click on the file on your desktop and choose "extract here".

Click on the newly extracted folder and to start the game choose "assaultcube.sh

---

### Post by rossmc92 on 2009-04-08
But does this explain the odd activities happening? I've never had this problem with my mates computer and thats got lower specs than this.

[Edit]
Just managed to setup a quick game on Open Arena before the menu had time to disappear. It runs perfectly fine, no problems whatsoever. There must be another reason for this.

---

### Post by crazyfuturamanoob on 2009-04-09
Maybe disable compiz?

---

### Post by binbash on 2009-04-09
Did you disable compiz?

---

### Post by rossmc92 on 2009-04-09
> **binbash said:**
> Did you disable compiz?

Yes, using metacity --replace. This is really kinda inconvenient though. It'll do fine but a better fix would be much appreciated. At least I now know Compiz is the problem.

---

