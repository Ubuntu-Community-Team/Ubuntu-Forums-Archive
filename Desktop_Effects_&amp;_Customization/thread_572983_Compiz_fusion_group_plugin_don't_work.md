---
title: "Compiz fusion group plugin don't work"
date: 2007-10-11
forum: Desktop Effects &amp; Customization
---

### Post by Niscrome on 2007-10-11
When I try to use the group/tab plug in, the key bindings won't work or when I <super> g my system freeze up then I have to <crtl><alt>backspace to restart to login. Also the <Shift><Super>Button1 don't work either.

I installed [compiz-fusion by Treviño](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/) on a Dell Inspiron 6000 1.5 ghz Intel Pentium M Processor

---

### Post by Niscrome on 2007-10-15
Can someone PLEASE help me. It had been 4 days since I post this thread and I would like to use the group plugin. Thank You.[-o<

---

### Post by santiagoward2000 on 2007-10-15
That's weird. I used Treviño's repos too, and had no problem. What video card are you using and how much RAM do you have?

---

### Post by Niscrome on 2007-10-16
I am not sure what video card I have but I know it is not ATI nor Nvidia and I have 512 mb of ram. Is there a way to get the specs on what graphic card I have?

---

### Post by cudaman73 on 2007-10-16
> **Niscrome said:**
> I am not sure what video card I have but I know it is not ATI nor Nvidia and I have 512 mb of ram. Is there a way to get the specs on what graphic card I have?

Can you paste the contents of 

```
$ lspci
```

Here?

---

### Post by Niscrome on 2007-10-16
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

```

---

### Post by xi3 on 2007-10-16
Looks like a built in laptop Intel Video card by the:

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

I tend to think support for intel video cards sometimes is hard though you might be able to find experimental drivers. Whats the brand name of the laptop have you tried googling yet to see if you can find linux drivers for it somewhere?

Regards,

Xi

---

### Post by Niscrome on 2007-10-16
> I tend to think support for intel video cards sometimes is hard though you might be able to find experimental drivers. Whats the brand name of the laptop have you tried googling yet to see if you can find linux drivers for it somewhere?


I'll see what I can find but I don't know about experimental drivers....

---

