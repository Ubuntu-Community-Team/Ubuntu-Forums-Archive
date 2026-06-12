---
title: "Gnome 3 Artifacts within status menu and calendar"
date: 2011-06-01
forum: Desktop Environments
---

### Post by imacQ on 2011-06-01
Natty with Gnome 3 from PPA. 
Adwaita default theme - On hover/mouseover in the status menu:

[IMG]http://artattackcentral.com/wordpress/wp-content/uploads/2011/06/statusMenuArtifacts.png[/IMG]

Also, I get this when using Alt/F2 for commands: 

[IMG]http://artattackcentral.com/wordpress/wp-content/uploads/2011/06/altF2artifacts.png[/IMG]

The drop down calendar also has "tiny boxes" instead of numbers. 

Have tried changing themes (the only answer "out there", which I found on the Arch forums). The DeviantArt theme works without artifacts - except!! the sound applet in the panel crashes gnome. 


lspci:
```
00:00.0 Host bridge: Intel Corporation E7205 Memory Controller Hub (rev 03)
00:00.1 Unassigned class [ff00]: Intel Corporation E7505/E7205 Series RAS Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation E7505/E7205 PCI-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV28GL [Quadro4 980 XGL] (rev a1)
02:03.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
02:05.0 SCSI storage controller: Adaptec AIC-7901A U320 (rev 03)
02:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

Installed Arch and Gnome 3 on a separate partition, and still experience exactly the same conditions with the font artifacts on Arch. Therefore it's not a Ubuntu or Arch issue, but rather Gnome 3 and the likely suspect is the video card. I'm using the nouveau driver.

Perhaps I could remove the sound applet from the panel, and be happy with the DeviantArt theme. 

Advice/thoughts/ideas/suggestions... appreciated. Thanks

---

### Post by D-Tux on 2011-10-17
I have the same problem. +my panel is also full whit artifacts.

Ubuntu 11.10

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]
01:00.1 Audio device: ATI Technologies Inc RV630/M76 audio device [Radeon HD 2600 Series]
02:06.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b9)
02:06.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 03)
02:06.3 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 20)

---

### Post by loconet on 2011-10-30
I'm having the exact same problem with 11.10. Any news on this? :(

Edit:

For anyone who stumbles upon this post, updating to the latest ATI binary driver fixed the problem (both 11.9 and 11.10 worked).

---

