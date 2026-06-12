---
title: "Help getting past text while booting up."
date: 2011-09-29
forum: Desktop Environments
---

### Post by speculater on 2011-09-29
For the love of Zeus help :-(  

I just recently lost my old 500gb HDD due to "imminent failure".  Nothing else has changed on this PC, except for now I can't get past the text that loads before the Desktop once I've installed nvidia proprietary drivers.  I've tried about a dozen different methods, nothing is working.  Attached are my most recent xorg logs.

The only way for me to regain control of my PC is to: 

alt+ctrl+f1

sudo apt-get remove --purge nvidia*

reboot




Otherwise I'm stuck at either "*Checking battery state" or "Stopping Userspace bootsplash"

my lspci is:

speculater@OldFaithful:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
04:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)



If anyone can shed some light on this I will greatly appreciate your help!  I've spent about 11 hours trying to get this working before coming forward to bother anyone.

Let me know if more logs are needed.

---

### Post by speculater on 2011-09-29
bumpily bump.:guitar:

---

