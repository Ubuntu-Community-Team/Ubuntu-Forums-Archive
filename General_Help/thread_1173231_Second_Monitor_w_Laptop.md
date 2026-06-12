---
title: "Second Monitor w/ Laptop"
date: 2009-05-29
forum: General Help
---

### Post by chrisruls00 on 2009-05-29
I just got a brand new HP Laptop. I had an old unused monitor and the laptop has a VGA port, so I wanted to try and get a dual monitor setup working. I can use system settings to detect it and chose a resolution, but the 2nd monitor is just a copy of my laptop's. I wanted another desktop so I can multi-task better, how do I set it up for this?

---

### Post by Mirge on 2009-05-29
Need specs please

---

### Post by chrisruls00 on 2009-05-29
Sorry, I had to find the box.

```

HP G60-235DX
Intel Pentium Dual-Core Mobile Processor T4200 (2.0 GHz)

```

Hmm, the box doesn't seem to tell what video card I have. Is there an application that can tell me? I seem to remember having an application like that on my last laptop...

EDIT: The HP website says my Video Graphics are "Intel Graphics Media Accelerator 4500M"

---

### Post by Mirge on 2009-05-29
lspci

---

### Post by chrisruls00 on 2009-05-29
lspci gives me:

```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                   
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)                                            
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

---

### Post by binary10 on 2009-05-29
> **chrisruls00 said:**
> I just got a brand new HP Laptop. I had an old unused monitor and the laptop has a VGA port, so I wanted to try and get a dual monitor setup working. I can use system settings to detect it and chose a resolution, but the 2nd monitor is just a copy of my laptop's. I wanted another desktop so I can multi-task better, how do I set it up for this?

Sounds like it's part way there - at least you've got some output coming from the vga port.
This might sound a bit basic but have you checked your 'Preferences->Display' and made sure you've not got the 'mirrored screens' checked ? 
I had a little blush when I spotted this on my old dual output ati card, after which fiddling around with detect screens and moving them around, I was then sorted.
worth a try.

---

### Post by chrisruls00 on 2009-05-29
I don't see any "Mirrored Screens" option in the KDE4.0 system settings, is there another program I should be using to try and do this?

---

