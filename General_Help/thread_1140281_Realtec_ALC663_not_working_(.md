---
title: "Realtec ALC663 not working :("
date: 2009-04-27
forum: General Help
---

### Post by Pasdar on 2009-04-27
I have the speaker icon in the top right taskbar, it even shows the name of it "HDA ATI SB - ALC663 Analog (pulseaudio Mixer)" but I have no audio.

**aplay -l shows:**
```
aplay: device_list:217: no soundcards found...
```

**lspci -v shows:**
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 0
	Capabilities: <access denied>

00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fdb00000-fdcfffff
	Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Memory behind bridge: fde00000-fdefffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdf00000-fdffffff
	Prefetchable memory behind bridge: 00000000f9f00000-00000000f9ffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=07, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fe000000-feafffff
	Prefetchable memory behind bridge: 00000000fa000000-00000000fcffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 1117
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at a000 [size=8]
	I/O ports at 9000 [size=4]
	I/O ports at 8000 [size=8]
	I/O ports at 7000 [size=4]
	I/O ports at 6000 [size=16]
	Memory at fdaff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fdafe000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at fdafd000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
	Memory at fdaff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fdafc000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fdafb000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdafa800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: 66MHz, medium devsel
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ff00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: ASUSTeK Computer Inc. Device 19d3
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fdaf4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
	Memory behind bridge: feb00000-febfffff

00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 11e7
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
	Memory at fdaf9000 (32-bit, non-prefetchable) [size=4K]
	Kernel driver in use: ohci_hcd

00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>

00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
	Flags: fast devsel

01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
	Subsystem: ASUSTeK Computer Inc. Device 1062
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at b000 [size=256]
	Memory at fdcf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

02:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
	Subsystem: ASUSTeK Computer Inc. Device 1875
	Flags: bus master, fast devsel, latency 0, IRQ 2297
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at c000 [size=256]
	Memory at fddf0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fddc0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx

02:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Subsystem: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fddec000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Device 1a3b:1067
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fdef0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 16d5
	Flags: bus master, fast devsel, latency 0, IRQ 2298
	I/O ports at d800 [size=256]
	Memory at f9fff000 (64-bit, prefetchable) [size=4K]
	Memory at f9fe0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at fdff0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

08:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 1877
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at febff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Subsystem: ASUSTeK Computer Inc. Device 1877
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1877
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at febff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device 1877
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at febfec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
```



I tried installing the linux drivers from realtek website, but it fails to compile because it says alsaconf is missing, I then read it use to be in Ubuntu but the developers decided to remove it... etc.. I don't know what to do...

anyone help? :(

---

### Post by Pasdar on 2009-04-27
Okay, after purging and reinstalling the following packs: linux-sound-base alsa-base alsa-utils

I got aplay to list it:
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

However, I still have no audio... :/

---

### Post by Pasdar on 2009-04-27
Problem solved.
```
# Please try this procedure:

# Step 1: Open Terminal from "Applications->Accessories->
Terminal"

#Step 2: Run the following command (copy/paste each command into the Terminal and then hit <enter>)

sudo gedit /etc/modprobe.d/alsa-base

# Add the following 5 lines to the end of the alsa-base file:

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=m51va
options snd-hda-intel enable_msi=1

# Run the following command (copy/paste each command into the Terminal and then hit <enter>)

sudo gedit /etc/modprobe.d/options

# Add the following 5 lines to the end of the options file:

options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=m51va
options snd-hda-intel enable_msi=1

# Step 3: Reboot pc and retest sound.

# Step 4: If audio output still does not work, please try one of the following model options (instead of m51va):

 ALC662/663
   3stack-dig 3-stack (2-channel) with SPDIF
   3stack-6ch 3-stack (6-channel)
   3stack-6ch-dig 3-stack (6-channel) with SPDIF
   6stack-dig 6-stack with SPDIF
   lenovo-101e Lenovo laptop
   eeepc-p701 ASUS Eeepc P701
   eeepc-ep20 ASUS Eeepc EP20
   m51va ASUS M51VA
   g71v ASUS G71V
   h13 ASUS H13
   g50v ASUS G50V
   auto auto-config reading BIOS (default)
```
[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65752](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/65752)

I don't even have an ASUS m51va, however I figured a soundcard is a soundcard, it should work... and it did work.

---

### Post by yax51 on 2010-03-11
Hello. I am also having this issue where my ALC63 card isn't working. When I run the command, sudo gedit /ect/modprob.d/alsa-base, there is nothing there. but I can open the same file in gedit manually. When I put the option code listed in the solution at the end of the file, I am unable to open or find the options file that I am suppose to open next. I new to Lnux, and only have a basic understanding of whats going on, but this doesn't seem right. if anyone could please help me on this I would be eternally grateful. Thanks!!

P.S. I am running Ubuntu 9.10 on a ASUS G50VT Laptop with Realtek HD audio

---

### Post by yax51 on 2010-03-11
Hello. I am also having this issue where my ALC663 card isn't working. When I run the command, sudo gedit /ect/modprob.d/alsa-base, there is nothing there. but I can open the same file in gedit manually. When I put the option code listed in the solution at the end of the file, I am unable to open or find the options file that I am suppose to open next. I new to Linux, and only have a basic understanding of whats going on, but this doesn't seem right. if anyone could please help me on this I would be eternally grateful. Thanks!!

P.S. I am running Ubuntu 9.10 on a ASUS G50VT laptop, with Realtek HD audio

---

### Post by yax51 on 2010-03-11
Sorry didnt mean to double post.....

---

### Post by Method X on 2010-03-11
Funny, i have the same problem at my home PC.
Audio doesn't work, even on Windows (XP, Vista, Seven). Its Asus M3A78-EMH HDMI.

I think something wrong with it, because i cant install(run) drivers in Windows.
and also
```
no sound device
```
in Linux.

I'm so happy i have a Thinkpad laptop :popcorn:

---

