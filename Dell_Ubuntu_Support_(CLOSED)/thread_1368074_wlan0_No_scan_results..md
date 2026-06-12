---
title: "wlan0 No scan results."
date: 2009-12-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sting3r on 2009-12-30
Hi everyone, I ran into this odd issue with my E6400 and Kubuntu. I installed KDE over my GNOME (9.10) and everything worked fine. not sure what changed but about a week later I lost my wlan0 interface. since I can see my wireless when running lshw I added iface wlan0 inet dhcp and auto wlan0 to the interfaces restarted networking and made sure its up. the problem now is when I run iwlist wlan0 scanning it always return with: wlan0     No scan results.

any ideas?

```
lspci -k                                                                         
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                      
        Kernel modules: intel-agp                                                                                  
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)                   
        Kernel driver in use: pcieport-driver                                                                      
        Kernel modules: shpchp                                                                                     
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)                         
        Kernel driver in use: e1000e                                                                               
        Kernel modules: e1000e                                                                                     
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)                     
        Kernel driver in use: uhci_hcd                                                                             
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)                     
        Kernel driver in use: uhci_hcd                                                                             
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)                     
        Kernel driver in use: uhci_hcd                                                                             
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)                    
        Kernel driver in use: ehci_hcd                                                                             
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)                          
        Kernel driver in use: HDA Intel                                                                            
        Kernel modules: snd-hda-intel                                                                              
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)                             
        Kernel driver in use: pcieport-driver                                                                      
        Kernel modules: shpchp                                                                                     
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)                             
        Kernel driver in use: pcieport-driver                                                                      
        Kernel modules: shpchp                                                                                     
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)                             
        Kernel driver in use: pcieport-driver                                                                      
        Kernel modules: shpchp                                                                                     
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)                             
        Kernel driver in use: pcieport-driver                                                                      
        Kernel modules: shpchp                                                                                     
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)                     
        Kernel driver in use: uhci_hcd                                                                             
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)                     
        Kernel driver in use: uhci_hcd                                                                             
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)                     
        Kernel driver in use: uhci_hcd                                                                             
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)                    
        Kernel driver in use: ehci_hcd                                                                             
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)                                             
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)                                    
        Kernel modules: iTCO_wdt                                                                                   
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 03)                          
        Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
        Kernel modules: i2c-i801
01:00.0 VGA compatible controller: nVidia Corporation G98M [Quadro NVS 160M] (rev a1)
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidiafb
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
        Kernel driver in use: ohci1394
        Kernel modules: firewire-ohci, ohci1394
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
        Kernel driver in use: sdhci-pci
        Kernel modules: sdhci-pci
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
        Kernel driver in use: ricoh-mmc
        Kernel modules: ricoh_mmc
0c:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
```

---

### Post by sting3r on 2009-12-30
I Just got it to work! Here is what I did:

1. Remove the old Wireless connections from the KDE network manager. By doing that I was able to run iwlist again.. (not sure why).
2. Remove the WLAN0 setting I added to /etc/network/interfaces. Doing that allowed KDE network manager to manage my wireless connections again.
3. restart X.

Now I'm back in business!

---

