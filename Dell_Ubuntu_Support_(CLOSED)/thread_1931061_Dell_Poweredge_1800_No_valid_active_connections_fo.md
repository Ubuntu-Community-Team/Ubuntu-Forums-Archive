---
title: "Dell Poweredge 1800 No valid active connections found! Wired"
date: 2012-02-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by raxhunter on 2012-02-24
First I would like to thank every one who helped me get my server up and running with UBUNTU GUI.
Now comes my second question :razz:  I am currently running UBUNTU 11.10 with the GUI. I am wanting to use  my server to serve media such as pictures music and home movies with  mostly family and friends. I have done some research and it should be  fairly easy to set up, but my UBUNTU sez I dont have a connection.  I go  to connection information and I get this error "No valid active  connections found!" my server is wired into my Cisco router. I  understand that i need to be able to look at my connection info to get  my server to do what I would like it to do... I know I have a connection  as I am posting this from my server. 

Any Ideas?

robert@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation E7520 Memory Controller Hub (rev 09)
00:02.0 PCI bridge: Intel Corporation E7525/E7520/E7320 PCI Express Port A (rev 09)
00:04.0 PCI bridge: Intel Corporation E7525/E7520 PCI Express Port B (rev 09)
00:06.0 PCI bridge: Intel Corporation E7520 PCI Express Port C (rev 09)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
01:00.0 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge A (rev 09)
01:00.2 PCI bridge: Intel Corporation 6700PXH PCI Express-to-PCI Bridge B (rev 09)
02:04.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 0:cool:
[COLOR=Red]03:07.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller (rev 05)[/COLOR]
03:09.0 RAID bus controller: Adaptec AAC-RAID (rev 01)
06:03.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
06:05.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
robert@ubuntu:~$ 

I done a search using google, of the red highlighted color and UBUNTU,  but am unsure if there is an update and how to get the update if needed.   Its wierd as I said before I am using my server to post this stuff... I  would think if my adapter wasnt working I wouldnt have internet on this  station.

---

