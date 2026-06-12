---
title: "Screen resolution."
date: 2009-02-12
forum: General Help
---

### Post by ex-para on 2009-02-12
Just loaded ubuntu hardy on a wide screen laptop, the screen resolution only has two options neither are any good so the question is how do I get the correct one or a better choice.

Any info will be appreciated.

---

### Post by spcwingo on 2009-02-12
You might need to enable a restricted driver.  Please post the output of:

```
lspci
```

---

### Post by ex-para on 2009-02-12
Thanks for the reply.

papion@papion-laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0d.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
00:0d.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
00:0d.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller
00:0d.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 09)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
06:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
papion@papion-laptop:~$

---

### Post by itendo on 2009-02-12
when you say "aren't any good" you mean theyre in non 16:9/10 format right? I had the same issue with my dell 700m with gutsy, but hardy fixed it. nonetheless, you may want to begin by also providing your xorg.conf that involves your monitor:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
```


below is a similar sounding thread for your problem unless i am completely mis-reading it: [Solved Screen Resolution ]("http://ubuntuforums.org/showthread.php?t=832000&highlight=screen+resolutions")

---

### Post by spcwingo on 2009-02-12
Looks like you're going to have to hand edit xorg.conf.  I'm not very good at that (I've only done one), so I suggest you hang around until someone with more experience in this comes along.  Like itendo has mentioned, you might want to go ahead and post your xorg.conf.  It's located in /etc/X11/  I'm sorry I can't be of more help.

---

