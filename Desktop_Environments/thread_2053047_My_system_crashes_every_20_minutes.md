---
title: "My system crashes every 20 minutes"
date: 2012-09-04
forum: Desktop Environments
---

### Post by shahverdy on 2012-09-04
Dear all
I have a problem with Gnome-shell, unity, Kde and any other desktop environment witch does require visual effects. The problem is that system crashes for about 30 seconds and this problem repeats again and again every 20 minutes, even less :( 
I have tested Ubuntu and Mint

When I use gnome classic I can use my system properly.

How can I solve this ?

---

### Post by Kognit on 2012-09-04
What is your hardware specifics: graphic card, CPU, RAM,...
Post output of:
> lspci -vv

My wild guess is that your system is too old to cope with that DEs. You could try LXDE or XFCE.

---

### Post by shahverdy on 2012-09-04
> **Kognit said:**
> What is your hardware specifics: graphic card, CPU, RAM,...
Post output of:


My wild guess is that your system is too old to cope with that DEs. You could try LXDE or XFCE.


Here it is ...
I don't think that it is so ...

```


00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
	Subsystem: NVIDIA Corporation Device cb79
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
	Subsystem: NVIDIA Corporation Device cb79
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: I/O ports at 4f00 [size=256]

00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 14
	Region 0: I/O ports at 4900 [size=64]
	Region 4: I/O ports at 4d00 [size=64]
	Region 5: I/O ports at 4e00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
	Subsystem: NVIDIA Corporation Device cb79
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 23
	Region 0: Memory at fae80000 (32-bit, non-prefetchable) [size=512K]
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current_updates, nvidia_current

00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fae7f000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 23
	Region 0: Memory at fae7ec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fae7d000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1) (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 21
	Region 0: Memory at fae7e800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: ASUSTeK Computer Inc. Device 12e3
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1) (prog-if 01 [Subtractive decode])
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>

00:0b.0 SATA controller: NVIDIA Corporation MCP79 AHCI Controller (rev b1) (prog-if 01 [AHCI 1.0])
	Subsystem: ASUSTeK Computer Inc. Device 1fa7
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 40
	Region 0: I/O ports at c080 [size=8]
	Region 1: I/O ports at c000 [size=4]
	Region 2: I/O ports at bc00 [size=8]
	Region 3: I/O ports at b880 [size=4]
	Region 4: I/O ports at b800 [size=16]
	Region 5: Memory at fae76000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: faf00000-fbffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000f7ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fea00000-feafffff
	Prefetchable memory behind bridge: 00000000f9f00000-00000000f9ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1) (prog-if 00 [Normal decode])
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Memory behind bridge: feb00000-febfffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 310M] (rev a2) (prog-if 00 [VGA controller])
	Subsystem: ASUSTeK Computer Inc. Device 1c22
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Region 3: Memory at f6000000 (64-bit, prefetchable) [size=32M]
	Region 5: I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at faf80000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia_current_updates, nvidia_current, nouveau, nvidiafb

02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 1c22
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at faf7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 41
	Region 0: I/O ports at e800 [size=256]
	Region 2: Memory at f9fff000 (64-bit, prefetchable) [size=4K]
	Region 4: Memory at f9ff8000 (64-bit, prefetchable) [size=16K]
	Expansion ROM at feaf0000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

04:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at febf0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k




```

---

### Post by kimberlite on 2012-09-05
Run a memory test, as describe here:
[https://help.ubuntu.com/community/MemoryTest]("https://help.ubuntu.com/community/MemoryTest")

---

### Post by SlugSlug on 2012-09-05
is your laptop getting hot?

---

### Post by shahverdy on 2012-09-05
> **SlugSlug said:**
> is your laptop getting hot?

No ...

---

### Post by Epodx64 on 2012-09-07
Is that an Integrated Nvidia card? I had an MCP 61 Geforce 6150se Nforce 430 Mobo and had nearly the same problem I could log in but it would either freeze or draw windows incredibly slow to the point of being unusable In mint Nouveau was to blame and wrecked havoc on my system when I was using ubuntu (kubuntu) the Nvidia Driver simply didn't work 295.xx my work around was this I booted to the login in screen then hit ctrl+alt+F1 to get to TTY1 console login and do this

sudo add-apt-repository ppa: x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

that will install the 304.x driver which works 100% better.

---

### Post by shahverdy on 2012-09-07
> **Epodx64 said:**
> Is that an Integrated Nvidia card?

No, just a simple Gforce 310M Cuda, with 512 MB ram


> **Epodx64 said:**
>  hit ctrl+alt+F1 to get to TTY1 console  

I Always do the same :(


> **Epodx64 said:**
> 

sudo add-apt-repository ppa: x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

that will install the 304.x driver which works 100% better.

I did this and then after that "gdm" wouldn't start. So I removed it and tried to install nvidia-current-updates from that repository. But after that I couldn't use Gnome-shell nor unity nor cinnamon. So I removed that too.

---

### Post by Epodx64 on 2012-09-07
> **shahverdy said:**
> No, just a simple Gforce 310M Cuda, with 512 MB ram


 

I Always do the same :(




I did this and then after that "gdm" wouldn't start. So I removed it and tried to install nvidia-current-updates from that repository. But after that I couldn't use Gnome-shell nor unity nor cinnamon. So I removed that too.

hmm... maybe try installing them from Jockey instead? the 304 driver should work far better then the regressed 29x series.

---

### Post by shahverdy on 2012-09-07
> **Epodx64 said:**
> hmm... maybe try installing them from Jockey instead? the 304 driver should work far better then the regressed 29x series.


I downloaded NVIDIA-Linux-x86-304.43.run from nvidia.com and installed KDM (I had it, but had removed it)and now I can work with unity. It seems it is working fine ;)  I must wait ...

---

