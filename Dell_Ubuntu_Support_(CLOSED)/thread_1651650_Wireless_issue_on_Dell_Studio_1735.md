---
title: "Wireless issue on Dell Studio 1735"
date: 2010-12-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by deverysturges on 2010-12-23
Installed Ubuntu (I remember selecting "wireless" as my connection type during the preinstall configuration), which initialized on my laptop without a hitch. 

I'm just unable to connect to my wireless network. Since I don't know how to identify my wireless security type (WEP, WEA, LEAP), I selected the first option in the security type drop-down menu, entered my key and wasn't presented with any "connect" radio button.

Could somebody point me in the direction of a list of instructions or some troubleshooting manual that could be of help to me?

---

### Post by mikewhatever on 2010-12-24
Hm..., isn't your wireless security type the one you picked when setting the router up? Anyway, one way to find out if it's WEP or WPA is to run **nm-tool** in a Terminal. The output will show all APs (access points) and their protection modes.

example:
> Wireless Access Points (* = current AP)
TP-LINK:  Infra, D8:5D:4C:C9:E6:B4, Freq 2422 MHz, Rate 54 Mb/s, Strength 40
LDESIGN:       Infra, 00:23:CD:F6:A1:32, Freq 2437 MHz, Rate 0 Mb/s, Strength 20 WEP


The first AP is unprotected and the second one is WEP protected.

Just to mention, Dell loves Broadcom wireless cards which require proprietary drivers. If you haven't done it yet, hook up an ethernet cable,then check out the Restricted Drivers utility under System->Administration.

---

