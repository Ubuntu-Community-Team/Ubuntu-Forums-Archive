---
title: "Ubuntu 10.10 64-bit not booting on Inspirion 1440"
date: 2011-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Hakukoru on 2011-01-12
Hi all, I recently purchased a [Dell Inspiron 1440]("http://www.bestbuy.com/site/Dell+-+Inspiron+Laptop+/+Intel%26%23174;+Pentium%26%23174;+Processor+/+14%22+Display+/+4GB+Memory+-+Mars+Black/1287179.p?id=1218247184996&skuId=1287179") from Best Buy and immediately replaced Windows 7 with Ubuntu 10.10. Unfortunately, I hadn't realized at the time that I could have installed the 64 bit version, so I am giving that a shot now... but after installing it will not boot. It's really strange as the 32-bit desktop version boots fine via live-usb and after full installation, and the 64-bit desktop version boots fine off of live-usb too, but not once it's installed (or to be specific, X never starts up, I get dumped to a terminal).

Any idea what the problem might be just based on the particular laptop? Or is there a log file getting dumped somewhere that might lead me in the right direction? Thanks in advance.

---

### Post by amsterdamharu on 2011-01-12
Could you post the output of the following commands?
```
lspci -k
```
Check the line that says VGA compatible controller and below Kernel driver in use:

And the output of:
```
cat /var/log//Xorg.0.log | grep EE
```

---

### Post by Hakukoru on 2011-01-12
"cat /var/log//Xorg.0.log | grep EE" gives me this:
> (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[186.175] (II) Loading Extension MIT-SCREEN-SAVER
[186.254] (EE) open /dev/fb0: No such file or directory

"lscpci -k" gives me this:
> 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
	Subsystem: Dell Device 0456
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
	Subsystem: Dell Device 0456
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
	Subsystem: Dell Device 0456
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
	Subsystem: Dell Device 0456
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
	Subsystem: Dell Device 0456
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
	Subsystem: Dell Device 0456
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
	Subsystem: Dell Device 0456
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
	Subsystem: Dell Device 0456
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
	Subsystem: Dell Device 0456
	Kernel modules: i2c-i801
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
	Subsystem: Dell Device 0456
	Kernel driver in use: intel ips
	Kernel modules: intel_ips
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
	Subsystem: Dell Device 0010
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Dell Device 0456
	Kernel driver in use: atl1c
	Kernel modules: atl1c
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
	Subsystem: Intel Corporation Device 8086

---

### Post by amsterdamharu on 2011-01-12
The Intel graphic controller doesn't need a xorg.cong per se. The quick fix when you're in the command line is to maybe (re)move the xorg.conf (if it's there at all).

```
mv /etc/X11/xorg.conf /etc/X11/xorg.old
```then try:

```
startx
```If that didn't work and you have a working cable Internet connection I'd advice to boot in recovery mode. Usually if you hold the shift key when you start up (just after the bios but before Ubuntu starts) there is a menu.
Choose Ubuntu recovery and then dpkg reconfigure.

I've seen other threads advice on installing 10.04 because the new kernel in 10.10 might have some problem with certain graphics controllers and with certain broadcom wireless cards, you can just try and see if you have the same problems and/or if they have been fixed already.

---

### Post by Hakukoru on 2011-01-13
Thanks for your help. Attempting to move the xorg.conf and starting X didn't help me, as xorg.conf did not exist. However, booting into recovery and running dpkg reconfiguration worked wonders. After about 30ish minutes of downloading and updating packages my laptop booted successfully :)

---

### Post by stanz on 2011-01-16
Awesome! :)

So its all good and solved?

---

