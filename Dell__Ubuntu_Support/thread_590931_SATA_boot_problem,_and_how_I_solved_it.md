---
title: "SATA boot problem, and how I solved it"
date: 2007-10-25
forum: Dell  Ubuntu Support
---

### Post by Tobu on 2007-10-25
The symptoms:
At boot, the initramfs was scanning SATA disks using the ata_piix kernel module, tried with slower speeds, and finally gave up with this error:
ata_hpa_resize: hpa sectors (0) is smaller that sectors (625142448).

This meant the machine was unbootable.

It also gave these other, possibly-related errors:
 * Failed to set xfermode.
 * IRQ #19 ignored - nobody cared.

What happened just before:
I resized a logical swap partition to make room for a new lvm partition.
Then the kernel found itself unable to re-read the partition table, I rebooted and got all these error messages.

What didn't happen just before:
I did not upgrade the kernel. The kernel was linux-image-2.6.22-14-generic at version 2.6.22-14.46, before and after the reboot.

The machine:
It's some kind of all-intel dell.
Says lspci:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)

```
The disk identifies itself as ST3320620AS .

The fix:
Boot into the Bios configuration (press F2); select "Integrated peripherials", set "Sata mode" to RAID instead of IDE. This has nothing to do with raid, but a different driver that ata_piix will be used, and all will be well.

Hope this helps someone, if it works for you please say it here!

---

### Post by pmeyerslu on 2007-11-06
tks
It seems to work out
:cool:

---

### Post by Tobu on 2007-11-06
Good.

I always fear this kind of stuff is a personal jinx :twisted:

---

### Post by pmeyerslu on 2007-11-07
do you know what happens when you change sata mode to Raid?

---

### Post by Tobu on 2007-11-07
Probably the motherboard enables a different chipset for SATA support?

As far as the brokenness in the original chipset, apparently it has only partial HPA support, and the kernel driver does uses HPA for more stuff since recent kernels.

---

### Post by Xav' on 2007-12-01
> **Tobu said:**
> The symptoms:
At boot, the initramfs was scanning SATA disks using the ata_piix kernel module, tried with slower speeds, and finally gave up with this error:
ata_hpa_resize: hpa sectors (0) is smaller that sectors (625142448).

This meant the machine was unbootable.

It also gave these other, possibly-related errors:
 * Failed to set xfermode.
 * IRQ #19 ignored - nobody cared.

What happened just before:
I resized a logical swap partition to make room for a new lvm partition.
Then the kernel found itself unable to re-read the partition table, I rebooted and got all these error messages.

What didn't happen just before:
I did not upgrade the kernel. The kernel was linux-image-2.6.22-14-generic at version 2.6.22-14.46, before and after the reboot.

The machine:
It's some kind of all-intel dell.
Says lspci:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)

```
The disk identifies itself as ST3320620AS .

The fix:
Boot into the Bios configuration (press F2); select "Integrated peripherials", set "Sata mode" to RAID instead of IDE. This has nothing to do with raid, but a different driver that ata_piix will be used, and all will be well.

Hope this helps someone, if it works for you please say it here!

Hi,

Well I tried that in case it would solve my "no sound" problem. My Kubuntu works fine but it didn't do anything to the sound problem.

---

### Post by Tentious on 2007-12-03
Awesome! This fixed my problem! Thanks for your post!

---

### Post by cacycleworks on 2007-12-03
> **Xav' said:**
> Hi,

Well I tried that in case it would solve my "no sound" problem. My Kubuntu works fine but it didn't do anything to the sound problem.

Maybe try seeing if your /var/log/dmesg says something about try "pci-assign-busses"

That [helped me with an issue before]("http://ubuntuforums.org/showthread.php?t=518702").

??? 

good luck,
Chris

---

