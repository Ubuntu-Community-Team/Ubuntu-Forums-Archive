---
title: "Install Madwifi drivers on Intell Pro/Wireless 2200 BG? WEP crack"
date: 2008-01-27
forum: Dell  Ubuntu Support
---

### Post by brettbed on 2008-01-27
Hi,

I am a noob at Ubuntu. I've read 100's of tutorials but it seems I can't get the right driver installed for my Intel Pro/Wireless card 2200 BG. I've been trying madwifi but maybe my card is just not supported. I've collected over 900,000 IVs and the crack still won't work. 

This is the tutorial I started with:

[http://mediakey.dk/~cc/hack-wireless-network-crack/](http://mediakey.dk/~cc/hack-wireless-network-crack/)

This is the error I get:

brettbed@brettbed-laptop:~$ sudo aircrack-ng -b 00:13:10:62:65:AD  dump-01.cap
Opening dump-01.cap
Read 7 packets.

No matching network found - check your bssid.

WTF


brettbed@brettbed-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
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
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Any help would be awesome!
:confused:
Thanks,

Brett

---

### Post by tturrisi on 2008-01-28
[http://www.aircrack-ng.org/doku.php?id=ipw2200](http://www.aircrack-ng.org/doku.php?id=ipw2200)

---

