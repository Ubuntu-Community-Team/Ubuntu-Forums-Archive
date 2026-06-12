---
title: "Suspend works two times, does not work afterwards"
date: 2008-01-05
forum: Desktop Environments
---

### Post by wild_oscar on 2008-01-05
I have an odd situation: I can suspend my machine two times without a problem. After the third, it won't suspend anymore.

I thought it was strange, but I googled and it seems someone else has the exact same problem:
[http://lists.tuxonice.net/lurker/message/20071208.131529.9043ec90.en.html]("http://lists.tuxonice.net/lurker/message/20071208.131529.9043ec90.en.html")

The problem seems to be the same:

dmesg:
```
[ 1775.216000] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000006) is beyond end of object [20070126]
[ 1775.216000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.PEX3.JMB1.SDE0._GTM] (Node df850270), AE_AML_PACKAGE_LIMIT
[ 1775.216000] ata7: ACPI get timing mode failed (AE 0x300d)
[ 1775.216000] pci_device_suspend(): ata_pci_device_suspend+0x0/0x40 [libata]() returns -22
[ 1775.216000] suspend_device(): pci_device_suspend+0x0/0x60() returns -22
[ 1775.216000] Could not suspend device 0000:03:00.1: error -22
[ 1775.216000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[ 1775.216000] pnp: Device 00:07 activated.
[ 1775.216000] pnp: Device 00:08 activated.
[ 1775.216000] pnp: Failed to activate device 00:09.

```

lspci:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

```

Any help appreciated!

---

### Post by poj on 2008-02-02
I have a similar problem, but have not counted the number of times I could suspend. I realised that the Jmicron PATA controller was to blame by reading your post.
If I run
```
modprobe -r pata_jmicron
```
It seems that it is possible to suspend the computer again.

You should append pata_jmicron to the list of modules to unload upon suspension, and things would most like work.

---

### Post by wild_oscar on 2008-02-02
> **poj said:**
> I have a similar problem, but have not counted the number of times I could suspend. I realised that the Jmicron PATA controller was to blame by reading your post.
If I run
```
modprobe -r pata_jmicron
```
It seems that it is possible to suspend the computer again.

You should append pata_jmicron to the list of modules to unload upon suspension, and things would most like work.

How did you test it?

If I try to remove it, I get:

FATAL: Module pata_jmicron is in use.

---

### Post by wild_oscar on 2008-02-02
Well, not much luck.

I added the module to /etc/default/acpi-support, but I still get the same problems:

1) it won't suspend after the 2nd time

2) IDE dvd recorder won't work after suspending the first time
> 
Feb  2 11:35:49 workbox kernel: [ 2707.152000] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000006) is beyond end of object [20070126]
Feb  2 11:35:49 workbox kernel: [ 2707.152000] ACPI Error (psparse-0551): Method parse/execution failed [\_SB_.PCI0.PEX3.JMB1.SDE0._GTM] (Node df850270), AE_AML_PACKAGE_LIMIT
Feb  2 11:35:49 workbox kernel: [ 2707.152000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 21
Feb  2 11:35:49 workbox kernel: [ 2707.152000] pnp: Device 00:07 activated.
Feb  2 11:35:49 workbox kernel: [ 2707.152000] pnp: Device 00:08 activated.
Feb  2 11:35:50 workbox kernel: [ 2707.300000] sd 2:0:0:0: [sda] Starting disk
Feb  2 11:35:50 workbox kernel: [ 2708.304000] sd 4:0:0:0: [sdb] Starting disk
Feb  2 11:35:50 workbox kernel: [ 2711.452000] QCM 3-2:1.0: no resume for driver QCM?
Feb  2 11:35:50 workbox kernel: [ 2711.452000] snd-usb-audio 3-2:1.1: no resume for driver snd-usb-audio?
Feb  2 11:35:50 workbox kernel: [ 2711.452000] snd-usb-audio 3-2:1.2: no resume for driver snd-usb-audio?
Feb  2 11:35:50 workbox kernel: [ 2711.556000] Restarting tasks ... done.


---

### Post by poj on 2008-02-02
> **wild_oscar said:**
> How did you test it?

If I try to remove it, I get:

FATAL: Module pata_jmicron is in use.

I tested it by just removing it and trying to suspend afterwards. The reason you get the error is that something else uses the module.

The reason for the burner not working after a while is most likely that not all modules used by the burner is reinserted correctly after resume.

Look at the output from lsmod before and after a suspend where the cd burner is not working.

---

