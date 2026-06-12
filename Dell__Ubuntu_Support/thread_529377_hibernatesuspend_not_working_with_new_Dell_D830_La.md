---
title: "hibernate/suspend not working with new Dell D830 Laptop"
date: 2007-08-19
forum: Dell  Ubuntu Support
---

### Post by pirx2 on 2007-08-19
Hi,

if I try to hibernate my D830 with Nvidia NVS 140M graphic, I end up with an blinking cursor in the upper left corner. I'm running xubuntu 7.04 with kernel 2.6.22-9-generic from the upcoming 7.10.

I already tried different options (NvAGP) in my xorg.conf, but this didn't  change anything. Unloading the nvidia, iwl4965 modules and executing hibernate on console gives the same result. I then have to reset the Laptop. 


lspci output:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0429 (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

/etc/default/acpi-support

> ACPI_SLEEP=true
ACPI_HIBERNATE=true
ACPI_SLEEP_MODE=mem
MODULES=""
MODULES_WHITELIST=""
SAVE_VBE_STATE=true
VBESTATE=/var/lib/acpi-support/vbestate
POST_VIDEO=true
USE_DPMS=true
HIBERNATE_MODE=shutdown
LOCK_SCREEN=true
STOP_SERVICES="mysql "
RESTART_IRDA=false
ENABLE_LAPTOP_MODE=false



Any ideas waht to check or how to debug the problem?

---

### Post by abadfish on 2007-08-19
I'm have a similar situation.  When I select suspend or hibernate, the screen saver just kicks in.  I was expecting the laptop to "shut down" like it does with Vista when I select suspend or hibernate.

anybody have any thoughts on how to make suspend/hibernate work???

---

### Post by pirx2 on 2007-08-19
I've now removed nearly all modules with rmmod and tried to hibernate from console. Still the same blinking cursor. Does it make a differerence if the module is removed after boot or not loaded during boot time at all?

---

### Post by pirx2 on 2007-08-25
update: with debian etch and kernel 2.6.18 + uwsusp hibernate is working. At least as long as the nvidia module is not loaded. I think this problem could be solved.

So why is it not working with ubuntu feisty, is it as general problem of newer kernels > 2.6.18?

---

### Post by bimbo on 2007-09-04
My D830 (with Intel GMA X3100) does go into suspend just fine, but upon wake up it freezes with a black screen with 2.6.22-10. 


Anyone know what to do about that?

---

