---
title: "flooded with message &quot;new high speed USB device using ehci_hcd and address XXX &quot;"
date: 2008-06-14
forum: Desktop Environments
---

### Post by alexsott on 2008-06-14
Hello,

I am getting indefinite flood of messages like this:


Jun 14 14:03:12 q kernel: [ 1351.951271] usb 1-1: new high speed USB device using ehci_hcd and address 96
Jun 14 14:03:12 q kernel: [ 1352.102899] usb 1-1: new high speed USB device using ehci_hcd and address 97
Jun 14 14:03:13 q kernel: [ 1352.254214] usb 1-1: new high speed USB device using ehci_hcd and address 98
Jun 14 14:03:13 q kernel: [ 1352.405066] usb 1-1: new high speed USB device using ehci_hcd and address 99
Jun 14 14:03:13 q kernel: [ 1352.555917] usb 1-1: new high speed USB device using ehci_hcd and address 100
Jun 14 14:03:14 q kernel: [ 1352.856362] usb 1-1: new high speed USB device using ehci_hcd and address 101
Jun 14 14:03:14 q kernel: [ 1353.188244] usb 1-1: new high speed USB device using ehci_hcd and address 102
Jun 14 14:03:14 q kernel: [ 1353.520114] usb 1-1: new high speed USB device using ehci_hcd and address 103
Jun 14 14:03:15 q kernel: [ 1353.850999] usb 1-1: new high speed USB device using ehci_hcd and address 104
Jun 14 14:03:15 q kernel: [ 1354.124277] usb 1-1: new high speed USB device using ehci_hcd and address 105
Jun 14 14:03:15 q kernel: [ 1354.395645] usb 1-1: new high speed USB device using ehci_hcd and address 106
Jun 14 14:03:16 q kernel: [ 1354.667979] usb 1-1: new high speed USB device using ehci_hcd and address 107
Jun 14 14:03:16 q kernel: [ 1354.937902] usb 1-1: new high speed USB device using ehci_hcd and address 108
Jun 14 14:03:16 q kernel: [ 1355.210254] usb 1-1: new high speed USB device using ehci_hcd and address 109
Jun 14 14:03:17 q kernel: [ 1355.480970] usb 1-1: new high speed USB device using ehci_hcd and address 110
Jun 14 14:03:17 q kernel: [ 1355.727157] usb 1-1: new high speed USB device using ehci_hcd and address 111
Jun 14 14:03:17 q kernel: [ 1355.998690] usb 1-1: new high speed USB device using ehci_hcd and address 112
Jun 14 14:03:18 q kernel: [ 1356.269416] usb 1-1: new high speed USB device using ehci_hcd and address 113
Jun 14 14:03:18 q kernel: [ 1356.541765] usb 1-1: new high speed USB device using ehci_hcd and address 114

Plugging in CF card - it is usually recognized only after many (like in 20) minutes. 

Other USB devices *apparenly* work slowly or slow to recognize *sometimes*.

I *think* it worked normal/better with previous versions. 

Any ideas, suggestions, advices?

Thanks,
~ Alex.

running Hardy Heron, nothing special
~$ uname -a
Linux reisling 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux

~$ lsusb
Bus 002 Device 005: ID 0566:3002 Monterey International Corp. 
Bus 002 Device 004: ID 046d:c03d Logitech, Inc. 
Bus 002 Device 002: ID 04f9:01ab Brother Industries, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

 lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:0a.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:0b.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

---

### Post by alexsott on 2008-06-23
Anyone?

---

### Post by rhoderickj on 2008-09-09
Interesting. I just noticed that I have the same problem. Did you figure out what the problem was? I know that disabling the ehci_hcd module gets rid of the constant error messages, but that really isn't helpful.

All of my hardware appears to work just fine, except for the massive logs in /var/log/. My output from lspci is very similar to yours. 

I'm searching for a bug report on this now. I'll file one if I can't find an existing one.

---

### Post by rhoderickj on 2008-09-09
There is a [bug filed for this in LaunchPad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88746"). I'm hoping that it will be fixed in Intrepid.

---

### Post by alexsott on 2008-09-09
Hmmm... after reading that bug & discussion, it does not look exactly the same to me ... I am not getting error messages - just those endless "new device" infos.
Will try to play with configurations, post my results here.

---

### Post by phaidros on 2008-12-07
any news on the issue?

I'm having this since intrepid with my thinkpad, and no (!) usb device works with high speed (usb sticks etc), only disabling ehci_hcd works, but gives only slow usb speed :(

---

### Post by leifg on 2009-07-14
I have the exact same problem on jaunty jackalope (I am using a logitech diNovo keyboard)

Is there any help for this?

---

