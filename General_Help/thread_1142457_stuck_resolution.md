---
title: "stuck resolution"
date: 2009-04-29
forum: General Help
---

### Post by morgan0 on 2009-04-29
hi, im sorry to be posting this, i have tried to search, but to no avail. 

so last night i installed ubuntu 9.04, but my resolution is stuck at a measly 640x400 or 640x350. the resiloution changer only lists these 2.

im using on board graphics, no gfx card or anything.


i read to type in a command to get some details that may help someone help me. last line is probably the one your after...

```
morgan@morgan-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. P4M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
morgan@morgan-desktop:~$ 
```sorry, its just a night mare to use anything like this, thats why ive resorted to posting here, i do hope someone can help me.

---

### Post by Bindsa on 2009-04-29
Looks like no proper drivers are installed, search Linux drivers for your card and install them, then retry.

Hope this helped you.

--
B!ndsa

---

### Post by morgan0 on 2009-04-29
hi Bindsa, i appreciate your rapid reply, sadly i dont really know what im doing. ive tried a few different options through synaptic package manager, but nothing helpeed. i tried to google a few different things, "linux VGA driver" , "VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)" etc, but ive no idea really what im looking for. 

i know its a lot to ask, but is there any chance you could do a quick search for me, or give me a nudge in the right direction.

it truly is quite difficult using firefox like this.

thank you, morgan

---

