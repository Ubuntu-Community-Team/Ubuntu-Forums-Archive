---
title: "Installing Wireless Adapter Drivers"
date: 2007-04-06
forum: Desktop Environments
---

### Post by ClickForth on 2007-04-06
I have a disc of Wireless Adapter drivers (it's PCI card) that I need to install to get on the interwebs. How do I install those/can I, on Ubuntu? When I put in the disc before it said it didn't know how to execute the setup.

---

### Post by ClickForth on 2007-04-06
I got some more information, and got a little further...

I have a  Belkin F5D7000, and according to the Wireless support, it should be detected out-of-box...but it's not, what can I do?

---

### Post by ZoiaGuyver on 2007-04-06
Normally you have to use the "ndiswrapper" to enable the cards (atleast i know you do with the 7050, which is a usb stick using the same chip).

Not sure if Ubuntu has it or whether its in the repo's, but i do have a link for the ndiswrapper site at sourceforge

[NdisWrapper](http://ndiswrapper.sourceforge.net/)

It says it support's your card

Card: Belkin 54g Wireless Desktop Network Card (F5D7000) 
Chipset: BCM4306 Board: V1799 D-7000 Rev 4.5 
pciid: 14e4:4320 
Driver: [http://www.belkin.com](http://www.belkin.com) 
Other: This is PCI, not cardbus. The chipset is marked BCM4306, however the supplied utility in win98 detects "BCM4306/BCM2050", and Linux utilities have variously reported; BCM4306, BCM4320, BCM94306. This card has been stable on a Slackware SMP system with ndiswrapper-0.8 since released, versions 0.7 and 0.9 do not work with the SMP kernel.

Maybe give that a try.

Id also check synaptic aswell just incase it is in the repo's

Hope this helps

---

