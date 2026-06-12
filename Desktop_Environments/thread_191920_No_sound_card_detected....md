---
title: "No sound card detected..."
date: 2006-06-08
forum: Desktop Environments
---

### Post by 3saul on 2006-06-08
I've done a fresh install of 6.06 with now sound card detected. I have installed all of the alsa packages (and also did this manually by installing alsa from source). I have an echo audio Darla 20. This worked no problem in Breezy. HAL can see the card:
[B]udi = '/org/freedesktop/Hal/devices/pci_1057_1801'
  info.udi = '/org/freedesktop/Hal/devices/pci_1057_1801'  (string)
  linux.subsystem = 'pci'  (string)
  linux.hotplug_type = 1  (0x1)  (int)
  pci.subsys_product = 'Darla'  (string)
  pci.subsys_vendor = 'Echo Digital Audio Corporation'  (string)
  info.product = 'DSP56301 Digital Signal Processor'  (string)
  pci.product = 'DSP56301 Digital Signal Processor'  (string)
  info.vendor = 'Motorola'  (string)
  pci.vendor = 'Motorola'  (string)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.device_class = 4  (0x4)  (int)
  pci.subsys_vendor_id = 60608  (0xecc0)  (int)
  pci.subsys_product_id = 16  (0x10)  (int)
  pci.vendor_id = 4183  (0x1057)  (int)
  pci.product_id = 6145  (0x1801)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0e.0/0000:02:06.0'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_ed'  (string)
  info.bus = 'pci'  (string)
  linux.sysfs_path_device = '/sys/devices/pci0000:00/0000:00:0e.0/0000:02:06.0'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:0e.0/0000:02:06.0'  (string)[/B]

---

