---
title: "Locking screen changes sound output device to headphones"
date: 2023-03-14
forum: Desktop Environments
---

### Post by Majki-Fajki on 2023-03-14
When screen gets locked, it switches audio output from HDMI to Headphones.

Please advise. 

```
michal@michal-Inspiron-13-5310:~$ lspci -k
0000:00:00.0 Host bridge: Intel Corporation 11th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
    Subsystem: Dell 11th Gen Core Processor Host Bridge/DRAM Registers
    Kernel modules: igen6_edac
0000:00:02.0 VGA compatible controller: Intel Corporation TigerLake-LP GT2 [Iris Xe Graphics] (rev 03)
    Subsystem: Dell TigerLake-LP GT2 [Iris Xe Graphics]
    Kernel driver in use: i915
    Kernel modules: i915
0000:00:04.0 Signal processing controller: Intel Corporation TigerLake-LP Dynamic Tuning Processor Participant (rev 02)
    Subsystem: Dell TigerLake-LP Dynamic Tuning Processor Participant
    Kernel driver in use: proc_thermal
    Kernel modules: processor_thermal_device_pci_legacy
0000:00:07.0 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #0 (rev 02)
    Kernel driver in use: pcieport
0000:00:07.1 PCI bridge: Intel Corporation Tiger Lake-LP Thunderbolt 4 PCI Express Root Port #1 (rev 02)
    Kernel driver in use: pcieport
0000:00:0d.0 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 USB Controller (rev 02)
    Subsystem: Dell Tiger Lake-LP Thunderbolt 4 USB Controller
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
0000:00:0d.2 USB controller: Intel Corporation Tiger Lake-LP Thunderbolt 4 NHI #0 (rev 02)
    Subsystem: Dell Tiger Lake-LP Thunderbolt 4 NHI
    Kernel driver in use: thunderbolt
    Kernel modules: thunderbolt
0000:00:0e.0 RAID bus controller: Intel Corporation Volume Management Device NVMe RAID Controller
    Subsystem: Dell Volume Management Device NVMe RAID Controller
    Kernel driver in use: vmd
    Kernel modules: vmd, ahci
0000:00:12.0 Serial controller: Intel Corporation Tiger Lake-LP Integrated Sensor Hub (rev 30)
    Subsystem: Dell Tiger Lake-LP Integrated Sensor Hub
    Kernel driver in use: intel_ish_ipc
    Kernel modules: intel_ish_ipc
0000:00:14.0 USB controller: Intel Corporation Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller (rev 30)
    Subsystem: Dell Tiger Lake-LP USB 3.2 Gen 2x1 xHCI Host Controller
    Kernel driver in use: xhci_hcd
    Kernel modules: xhci_pci
0000:00:14.2 RAM memory: Intel Corporation Tiger Lake-LP Shared SRAM (rev 30)
    Subsystem: Dell Tiger Lake-LP Shared SRAM
0000:00:14.3 Network controller: Intel Corporation Wi-Fi 6 AX201 (rev 30)
    Subsystem: Intel Corporation Wi-Fi 6 AX201
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
0000:00:15.0 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #0 (rev 30)
    Subsystem: Dell Tiger Lake-LP Serial IO I2C Controller
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
0000:00:15.1 Serial bus controller: Intel Corporation Tiger Lake-LP Serial IO I2C Controller #1 (rev 30)
    Subsystem: Dell Tiger Lake-LP Serial IO I2C Controller
    Kernel driver in use: intel-lpss
    Kernel modules: intel_lpss_pci
0000:00:16.0 Communication controller: Intel Corporation Tiger Lake-LP Management Engine Interface (rev 30)
    Subsystem: Dell Tiger Lake-LP Management Engine Interface
    Kernel driver in use: mei_me
    Kernel modules: mei_me
0000:00:1f.0 ISA bridge: Intel Corporation Tiger Lake-LP LPC Controller (rev 30)
    Subsystem: Dell Tiger Lake-LP LPC Controller
0000:00:1f.3 Multimedia audio controller: Intel Corporation Tiger Lake-LP Smart Sound Technology Audio Controller (rev 30)
    Subsystem: Dell Tiger Lake-LP Smart Sound Technology Audio Controller
    Kernel driver in use: sof-audio-pci-intel-tgl
    Kernel modules: snd_hda_intel, snd_sof_pci_intel_tgl
0000:00:1f.4 SMBus: Intel Corporation Tiger Lake-LP SMBus Controller (rev 30)
    Subsystem: Dell Tiger Lake-LP SMBus Controller
    Kernel driver in use: i801_smbus
    Kernel modules: i2c_i801
0000:00:1f.5 Serial bus controller: Intel Corporation Tiger Lake-LP SPI Controller (rev 30)
    Subsystem: Dell Tiger Lake-LP SPI Controller
10000:e0:1c.0 System peripheral: Intel Corporation Device 09ab
10000:e0:1c.4 PCI bridge: Intel Corporation Device a0bc (rev 30)
    Kernel driver in use: pcieport
10000:e1:00.0 Non-Volatile memory controller: Solid State Storage Technology Corporation Device 1007 (rev 03)
    Subsystem: Silicon Motion, Inc. Device 2267
    Kernel driver in use: nvme
    Kernel modules: nvme

```

---

