---
title: "dmesg stops updating /var/log/dmesg"
date: 2010-12-12
forum: Desktop Environments
---

### Post by teeedubb on 2010-12-12
I have noticed on my pc that dmesg stops updating /var/log/dmesg after a certain point, and will not update the logfile again until after a reboot. These are the last lines that appear in the dmesg logfile:

> [   10.695146] ppdev: user-space parallel port driver
[   10.753412] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.780970] EDAC MC: Ver: 2.1.0 Nov 24 2010
[   10.787220] shpchp 0000:00:01.0: HPC vendor_id 1022 device_id 9602 ss_vid 0 ss_did 0
[   10.787226] shpchp 0000:00:01.0: Cannot reserve MMIO region
[   10.787447] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.803614] EDAC amd64_edac:  Ver: 3.2.0 Nov 24 2010
[   10.803707] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   10.803715] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.803716]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.803718]  (Note that use of the override may cause unknown side effects.)
[   10.803738] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   10.812493] ACPI: resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0x000b00-0x000b0f]
[   10.812496] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.950957] md: bind<sde>
[   10.956376] md: bind<sdf>
[   11.301556] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   11.301562] Disabling lock debugging due to kernel taint
[   11.375181] [fglrx] Maximum main memory to use for locked dma buffers: 3551 MBytes.
[   11.375233] [fglrx]   vendor: 1002 device: 9710 count: 1
[   11.375664] [fglrx] ioport: bar 1, base 0xee00, size: 0x100
[   11.375679] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.375684] pci 0000:01:05.0: setting latency timer to 64
[   11.376071] [fglrx] Kernel PAT support is enabled
[   11.376100] [fglrx] module loaded - fglrx 8.79.4 [Oct 26 2010] with 1 minors
[   11.897828] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   11.897914] HDA Intel 0000:01:05.1: setting latency timer to 64
[   12.221917] r8169: eth0: link up
[   12.221924] r8169: eth0: link up
[   12.950016] type=1505 audit(1292145584.543:6):  operation="profile_replace" pid=1055 name="/sbin/dhclient3"
[   12.950265] type=1505 audit(1292145584.543:7):  operation="profile_replace" pid=1055 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.950414] type=1505 audit(1292145584.543:8)  operation="profile_replace" pid=1055 name="/usr/lib/connman/scripts/dhclient-script"
[   13.146284] type=1505 audit(1292145584.743:9):  operation="profile_load" pid=1056 name="/usr/sbin/mysqld"
[   13.148082] type=1505 audit(1292145584.743:10):  operation="profile_replace" pid=1057 name="/usr/sbin/ntpd"
[   13.251210] type=1505 audit(1292145584.843:11):  operation="profile_load" pid=1058 name="/usr/sbin/tcpdump"
[   15.922367] type=1505 audit(1292145587.523:12):  operation="profile_replace" pid=1228 name="/usr/sbin/mysqld"This has just happened recently, but there havent been any hardware changes or drastic software changes. Im running Ubuntu 10.04.1 that is current as of today. I have tried running 

```
sudo dpkg-reconfigure dmesg
```to no avail, and theres nothing in the logs that points to any errors. Is theres anyway I can reinstall dmesg? Or maybe perform something similar to the dpkg-reconfigure command?

I have also attached the following logfiles: dmesg, messages, syslog and daemon.

Any help will be greatly appreciated.

---

