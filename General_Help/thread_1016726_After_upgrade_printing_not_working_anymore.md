---
title: "After upgrade printing not working anymore"
date: 2008-12-20
forum: General Help
---

### Post by mdeinum on 2008-12-20
Small story: My printer (HP LaserJet 1000) doesn't work anymore.

Long Story: My HP LaserJet 1000 Printer worked like a charm in Ubuntu 8.04 and later also 8.10. However after upgrading to cups 1.3.9 (or it could be the latest kernel 2.6.27-11-generic) my printer doesn't print anymore.

Cups is running, tried stopping/restarting. Even tried uninstalling cups (and every side project) and reinstalling cups.

Printer is detected, shows up. According to the programmes the file is printed however nothing is coming from my printer (I also tried different progammes!). To make it even worse/stranger printing a test page DOES work. So currently the only thing I can print are test pages.

Sometimes I get the message 'printer 'x' might not be connected'. Currently this issue is driving me nuts (and I'm strongly considering moving back to windows if I cannot resolve it :s).

One thing I find strange/disturbing is the amount of messages in the /var/log/messages if I plugin my usb cable.

Here is the debug information as per [DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

mdeinum@mdeinum-t61:~/Downloads$ lsmod | grep usb
usbhid                 35840  0 
btusb                  19736  3 
usblp                  20480  0 
hid                    50560  1 usbhid
bluetooth              61924  11 bnep,sco,rfcomm,l2cap,btusb
usbcore               149360  6 usbhid,btusb,usblp,ehci_hcd,uhci_hcd

/var/log/messages
Dec 20 15:25:59 mdeinum-t61 kernel: [ 6129.844130] usb 2-1: new full speed USB device using uhci_hcd and address 34
Dec 20 15:25:59 mdeinum-t61 kernel: [ 6130.015091] usb 2-1: configuration #1 chosen from 1 choice
Dec 20 15:25:59 mdeinum-t61 logger: loading hp_laserjet_1000 firmware 002 034
Dec 20 15:25:59 mdeinum-t61 kernel: [ 6130.024094] usblp0: USB Bidirectional printer dev 34 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 20 15:25:59 mdeinum-t61 python: hp-firmware[7283]: warning: hp-firmware should not be run as root.
Dec 20 15:25:59 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Dec 20 15:26:00 mdeinum-t61 kernel: [ 6130.349198] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:00 mdeinum-t61 kernel: [ 6130.349225] usblp0: nonzero write bulk status received: -32
Dec 20 15:26:00 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: ... download failed.
Dec 20 15:26:05 mdeinum-t61 kernel: [ 6135.456535] usb 2-1: USB disconnect, address 34
Dec 20 15:26:05 mdeinum-t61 kernel: [ 6135.457629] usblp0: removed
Dec 20 15:26:05 mdeinum-t61 kernel: [ 6135.888127] usb 2-1: new full speed USB device using uhci_hcd and address 35
Dec 20 15:26:05 mdeinum-t61 kernel: [ 6136.063475] usb 2-1: configuration #1 chosen from 1 choice
Dec 20 15:26:05 mdeinum-t61 logger: loading hp_laserjet_1000 firmware 002 035
Dec 20 15:26:05 mdeinum-t61 kernel: [ 6136.072340] usblp0: USB Bidirectional printer dev 35 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 20 15:26:05 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Dec 20 15:26:05 mdeinum-t61 python: hp-firmware[7339]: warning: hp-firmware should not be run as root.
Dec 20 15:26:06 mdeinum-t61 kernel: [ 6136.373188] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:06 mdeinum-t61 kernel: [ 6136.373210] usblp0: nonzero write bulk status received: -32
Dec 20 15:26:06 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: ... download failed.
Dec 20 15:26:06 mdeinum-t61 kernel: [ 6136.878187] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:07 mdeinum-t61 python: hp-makeuri[7396]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:08 mdeinum-t61 python: hp-makeuri[7400]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:10 mdeinum-t61 kernel: [ 6140.648260] usb 2-1: USB disconnect, address 35
Dec 20 15:26:10 mdeinum-t61 kernel: [ 6140.648819] usblp0: removed
Dec 20 15:26:11 mdeinum-t61 kernel: [ 6141.384173] usb 2-1: new full speed USB device using uhci_hcd and address 36
Dec 20 15:26:11 mdeinum-t61 kernel: [ 6141.560098] usb 2-1: configuration #1 chosen from 1 choice
Dec 20 15:26:11 mdeinum-t61 logger: loading hp_laserjet_1000 firmware 002 036
Dec 20 15:26:11 mdeinum-t61 kernel: [ 6141.571104] usblp0: USB Bidirectional printer dev 36 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 20 15:26:11 mdeinum-t61 python: hp-firmware[7416]: warning: hp-firmware should not be run as root.
Dec 20 15:26:11 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Dec 20 15:26:11 mdeinum-t61 kernel: [ 6141.896166] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:11 mdeinum-t61 kernel: [ 6141.896186] usblp0: nonzero write bulk status received: -32
Dec 20 15:26:11 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: ... download failed.
Dec 20 15:26:12 mdeinum-t61 kernel: [ 6143.028157] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:13 mdeinum-t61 python: hp-makeuri[7474]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:14 mdeinum-t61 python: hp-makeuri[7478]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:15 mdeinum-t61 kernel: [ 6146.104253] usb 2-1: USB disconnect, address 36
Dec 20 15:26:15 mdeinum-t61 kernel: [ 6146.104809] usblp0: removed
Dec 20 15:26:16 mdeinum-t61 kernel: [ 6146.844054] usb 2-1: new full speed USB device using uhci_hcd and address 37
Dec 20 15:26:16 mdeinum-t61 kernel: [ 6147.015141] usb 2-1: configuration #1 chosen from 1 choice
Dec 20 15:26:16 mdeinum-t61 logger: loading hp_laserjet_1000 firmware 002 037
Dec 20 15:26:16 mdeinum-t61 kernel: [ 6147.026052] usblp0: USB Bidirectional printer dev 37 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 20 15:26:16 mdeinum-t61 python: hp-firmware[7494]: warning: hp-firmware should not be run as root.
Dec 20 15:26:16 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Dec 20 15:26:16 mdeinum-t61 kernel: [ 6147.310191] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:16 mdeinum-t61 kernel: [ 6147.310215] usblp0: nonzero write bulk status received: -32
Dec 20 15:26:17 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: ... download failed.
Dec 20 15:26:18 mdeinum-t61 kernel: [ 6148.555151] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:19 mdeinum-t61 python: hp-makeuri[7552]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:19 mdeinum-t61 python: hp-makeuri[7556]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:21 mdeinum-t61 kernel: [ 6151.560227] usb 2-1: USB disconnect, address 37
Dec 20 15:26:21 mdeinum-t61 kernel: [ 6151.564158] usblp0: removed
Dec 20 15:26:21 mdeinum-t61 kernel: [ 6152.296131] usb 2-1: new full speed USB device using uhci_hcd and address 38
Dec 20 15:26:22 mdeinum-t61 kernel: [ 6152.472113] usb 2-1: configuration #1 chosen from 1 choice
Dec 20 15:26:22 mdeinum-t61 logger: loading hp_laserjet_1000 firmware 002 038
Dec 20 15:26:22 mdeinum-t61 kernel: [ 6152.482031] usblp0: USB Bidirectional printer dev 38 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 20 15:26:22 mdeinum-t61 python: hp-firmware[7572]: warning: hp-firmware should not be run as root.
Dec 20 15:26:22 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Dec 20 15:26:22 mdeinum-t61 kernel: [ 6152.769159] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:22 mdeinum-t61 kernel: [ 6152.769179] usblp0: nonzero write bulk status received: -32
Dec 20 15:26:22 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: ... download failed.
Dec 20 15:26:23 mdeinum-t61 kernel: [ 6153.955156] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:24 mdeinum-t61 python: hp-makeuri[7630]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:25 mdeinum-t61 python: hp-makeuri[7634]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:26 mdeinum-t61 kernel: [ 6157.016262] usb 2-1: USB disconnect, address 38
Dec 20 15:26:26 mdeinum-t61 kernel: [ 6157.020163] usblp0: removed
Dec 20 15:26:27 mdeinum-t61 kernel: [ 6157.756182] usb 2-1: new full speed USB device using uhci_hcd and address 39
Dec 20 15:26:27 mdeinum-t61 kernel: [ 6157.988134] usb 2-1: configuration #1 chosen from 1 choice
Dec 20 15:26:27 mdeinum-t61 logger: loading hp_laserjet_1000 firmware 002 039
Dec 20 15:26:27 mdeinum-t61 kernel: [ 6158.001167] usblp0: USB Bidirectional printer dev 39 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 20 15:26:27 mdeinum-t61 python: hp-firmware[7650]: warning: hp-firmware should not be run as root.
Dec 20 15:26:27 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Dec 20 15:26:27 mdeinum-t61 kernel: [ 6158.293199] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:27 mdeinum-t61 kernel: [ 6158.293222] usblp0: nonzero write bulk status received: -32
Dec 20 15:26:27 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: ... download failed.
Dec 20 15:26:29 mdeinum-t61 kernel: [ 6159.492172] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:30 mdeinum-t61 python: hp-makeuri[7705]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:30 mdeinum-t61 python: hp-makeuri[7709]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:32 mdeinum-t61 kernel: [ 6162.472224] usb 2-1: USB disconnect, address 39
Dec 20 15:26:32 mdeinum-t61 kernel: [ 6162.475958] usblp0: removed
Dec 20 15:26:32 mdeinum-t61 kernel: [ 6163.208169] usb 2-1: new full speed USB device using uhci_hcd and address 40
Dec 20 15:26:33 mdeinum-t61 kernel: [ 6163.442478] usb 2-1: configuration #1 chosen from 1 choice
Dec 20 15:26:33 mdeinum-t61 kernel: [ 6163.449311] usblp0: USB Bidirectional printer dev 40 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 20 15:26:33 mdeinum-t61 logger: loading hp_laserjet_1000 firmware 002 040
Dec 20 15:26:33 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Dec 20 15:26:33 mdeinum-t61 python: hp-firmware[7725]: warning: hp-firmware should not be run as root.
Dec 20 15:26:33 mdeinum-t61 kernel: [ 6163.753192] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:33 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: ... download failed.
Dec 20 15:26:33 mdeinum-t61 kernel: [ 6163.753208] usblp0: nonzero write bulk status received: -32
Dec 20 15:26:34 mdeinum-t61 kernel: [ 6164.823171] usblp0: nonzero read bulk status received: -32
Dec 20 15:26:35 mdeinum-t61 python: hp-makeuri[7771]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:35 mdeinum-t61 python: hp-makeuri[7775]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:37 mdeinum-t61 kernel: [ 6167.928270] usb 2-1: USB disconnect, address 40
Dec 20 15:26:37 mdeinum-t61 kernel: [ 6167.928833] usblp0: removed
Dec 20 15:26:38 mdeinum-t61 kernel: [ 6168.664126] usb 2-1: new full speed USB device using uhci_hcd and address 41
Dec 20 15:26:38 mdeinum-t61 kernel: [ 6168.844518] usb 2-1: configuration #1 chosen from 1 choice
Dec 20 15:26:38 mdeinum-t61 kernel: [ 6168.853314] usblp0: USB Bidirectional printer dev 41 if 0 alt 0 proto 2 vid 0x03F0 pid 0x0517
Dec 20 15:26:38 mdeinum-t61 logger: loading hp_laserjet_1000 firmware 002 041
Dec 20 15:26:38 mdeinum-t61 python: hp-firmware[7791]: warning: hp-firmware should not be run as root.
Dec 20 15:26:38 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: loading HP LaserJet 1000 firmware /usr/share/foo2zjs/firmware/sihp1000.dl to /dev/usb/lp0 ...
Dec 20 15:26:38 mdeinum-t61 /etc/hotplug/usb/hplj1000: foo2zjs: ... download successful.
Dec 20 15:26:41 mdeinum-t61 python: hp-makeuri[7840]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:41 mdeinum-t61 python: hp-makeuri[7844]: warning: hp-makeuri should not be run as root.
Dec 20 15:26:41 mdeinum-t61 kernel: [ 6171.996511] usblp0: removed

mdeinum@mdeinum-t61:~/Downloads$ lpinfo -v
network socket
network beh
direct hal
direct hpfax
**direct hp:/usb/hp_LaserJet_1000?serial=0**
network http
network ipp
network lpd
direct scsi
network smb

If anyone has some pointers/hints/tips/workarounds to get my printer working again, much appreciated.

---

### Post by markovg on 2009-01-21
I was able to install my HP 1020 on xubuntu intrepid with the following process:

1) $ sudo apt-get install hplip-gui

2) Remove the printer via [http://localhost:631](http://localhost:631) or (xubuntu settings->printing)

3) Install the printer with
$ hp-setup

4) Run the HPLIP toolbox in Admin or Settings menu

5) Go to the actions tab for your printer and "Download Firmware"

The printer awoke, and would print test pages.

---

### Post by markovg on 2009-01-21
See also this launchpad answer:

[https://answers.launchpad.net/hplip/+question/39027]("https://answers.launchpad.net/hplip/+question/39027")

or perhaps this bug

[https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/217215]("https://bugs.launchpad.net/ubuntu/+source/hplip/+bug/217215")

---

