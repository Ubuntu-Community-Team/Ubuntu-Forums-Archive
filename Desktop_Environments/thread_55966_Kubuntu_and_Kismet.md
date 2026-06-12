---
title: "Kubuntu and Kismet"
date: 2005-08-10
forum: Desktop Environments
---

### Post by kilometers on 2005-08-10
I recently purchased an Orinoco Gold 802.11b card and have it up and running.  I want to download and install kismet using apt-get, but I seems to be too inept to do so.  I already have modified the sources.list file to include the "backdoor" list.  I need to use the exact name of the kismet distro I want right?

p.s. I already downloaded the current Orinoco patched tar (0.13-26) from kismet, but during the install a hermes.config cannot be located.

any ideas??

---

### Post by jshein on 2005-08-25
See my HowTo here

[http://ubuntuforums.org/showthread.php?t=23596](http://ubuntuforums.org/showthread.php?t=23596)

---

### Post by tonysathre on 2005-08-29
just use synaptic to get kismet and ethereal

---

### Post by kilometers on 2005-09-10
I have some free time, so I am going to try jshein's recommendation with the latest release of kismet 2005-08-R1.  Thanks and I'll let you know what happens.

---

### Post by kilometers on 2005-09-10
kilometers@KUBUNTU:/$ kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to kilometers (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (orinocosource): Enabling monitor mode for orinoco source interface eth1 channel 6...
FATAL: channel get ioctl failed 19:No such device

Can anyone help ....

---

### Post by jshein on 2005-09-12
Post the ouput of dmesg after you insert the wireless card. 

Looks like your card is not being identified as eth1 or possibly not at all.

---

### Post by kilometers on 2005-09-12
Here is my full dmesg output.  I guess my card is not being recognized?


lug
hw_random hardware driver 1.0.0 loaded
usbcore: registered new driver hiddev
input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(T
M)] on usb-0000:00:1d.0-2
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
ACPI: PCI interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.5 to 64
intel8x0_measure_ac97_clock: measured 50052 usecs
intel8x0: clocking to 48000
8139too Fast Ethernet driver 0.9.27
ACPI: PCI interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 20
eth0: RealTek RTL8139 at 0x3000, 00:c0:9f:42:ec:7f, IRQ 20
eth0:  Identified 8139 chip type 'RTL-8101'
8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
Linux Kernel Card Services
  options:  [pci] [cardbus] [pm]
ACPI: PCI interrupt 0000:02:01.0[A] -> GSI 17 (level, low) -> IRQ 17
Yenta: CardBus bridge found at 0000:02:01.0 [103c:006a]
Yenta: ISA IRQ mask 0x0000, PCI irq 17
Socket status: 30000006
ohci1394: $Rev: 1223 $ Ben Collins <bcollins@debian.org>
ACPI: PCI interrupt 0000:02:02.0[A] -> GSI 19 (level, low) -> IRQ 19
eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[d2007000-d20077ff]  Max
 Packet=[2048]
NET: Registered protocol family 17
ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00508b08800426c8]
NET: Registered protocol family 10
Disabled Privacy Extensions on device c0313ce0(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [ACAD] (on-line)
ACPI: Battery Slot [BAT1] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Sleep Button (CM) [SBTN]
ACPI: Lid Switch [LID]
ibm_acpi: ec object not found
ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
cs: IO port probe 0x0100-0x04ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
ibm_acpi: ec object not found
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
synaptics: using relaxed packet validation
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
NTFS-fs error (device hda1): ntfs_ucstonls(): Unicode name contains characters t
hat cannot be converted to character set cp437.
cs: memory probe 0xa0000000-0xa0ffffff: clean.
hermes: no version for "struct_module" found: kernel tainted.
orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski
@gnu.org>, et al)
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <pro
[email]ski@gnu.org[/email]>, et al)
orinoco_lock() called with hw_unavailable (dev=d8836000)
eth1: Station identity 001f:0001:0008:0048
eth1: Looks like a Lucent/Agere firmware version 8.72
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:02:2D:B5:60:B6
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 5.0, irq 17, io 0x0100-0x013f
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
eth1: no IPv6 routers present
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.

---

### Post by jshein on 2005-09-13
OK. 

For starters your card is being recognized.

[I]> orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski
@gnu.org>, et al)
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <pro
[email]ski@gnu.org[/email]>, et al)
orinoco_lock() called with hw_unavailable (dev=d8836000)
eth1: Station identity 001f:0001:0008:0048
eth1: Looks like a Lucent/Agere firmware version 8.72
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:02:2D:B5:60:B6
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 5.0, irq 17, io 0x0100-0x013f[/I]

But this is not good.

....
[I]> hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.
hermes @ IO 0x100: Card removed while issuing command.[/I]
... etc....

Do you have access to any other PCMCIA cards? If yes then insert it to ensure that the PCMCIA drivers or hardware are functioning properly. Look in the output of dmesg again to make sure that you do not get error messages as above.

Post your results and I will get back to you.

---

### Post by kilometers on 2005-09-13
I only have that Orinoco card.   Any suggestions?  Do I need to edit a config file?

---

### Post by jshein on 2005-09-14
My concern is that it seems that either your wireless card or pcmcia system is stopping functioning before you can actually use the card. The reason that I wanted you to somehow get any other pcmcia card is that by inserting another card, if it is detected and functions properly then pcmcia is good and you can assume it is a driver or card firmware issue. If you still get the same errors about the card being ejected, then there is a pcmcia issue that may only be corrected by recompiling the kernel, or modules, or upgrading to a newer kernel.

---

