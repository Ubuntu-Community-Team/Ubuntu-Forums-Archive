---
title: "Help USB ports not working"
date: 2009-03-01
forum: General Help
---

### Post by shateredsoul on 2009-03-01
HI.. so I did this

> chmod 644 usbcore.ko
sudo cp usbcore.ko /lib/modules/`uname -r`/kernel/drivers/usb/core
sudo depmod -ae
sudo update-initramfs -u
sudo reboot

because i was trying to get my virtual box to recognize my ipod.. but now ubuntu won't recognize usb devices.  The link to the blog is here, [http://forums.virtualbox.org/viewtopic.php?p=44025]("http://forums.virtualbox.org/viewtopic.php?p=44025")

Does anyone know what I did?

=(

---

### Post by shateredsoul on 2009-03-01
I have ubuntu 8.10

---

### Post by shateredsoul on 2009-03-01
omar@laptop:~$ dmesg |tail -n 20
[   18.807523] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.457777] ACPI: WMI: Mapper loaded
[   20.511358] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   20.586370] apm: BIOS not found.
[   20.792407] ppdev: user-space parallel port driver
[   24.308095] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   24.308107] vboxdrv: Successfully done.
[   24.308112] vboxdrv: Found 1 processor cores.
[   24.310940] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   24.310951] vboxdrv: Successfully loaded version 2.1.2 (interface 0x000a0009).
[   30.627402] [drm] Initialized drm 1.1.0 20060810
[   30.632783] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   30.632791] pci 0000:00:02.0: setting latency timer to 64
[   30.633848] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.697317] NET: Registered protocol family 17
[   58.440927] ieee80211_crypt: registered algorithm 'WEP'
[   64.381049] NET: Registered protocol family 10
[   64.382647] lo: Disabled Privacy Extensions
[   64.384422] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   74.492026] eth1: no IPv6 routers present

---

