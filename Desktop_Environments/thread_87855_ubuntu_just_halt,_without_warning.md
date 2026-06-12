---
title: "ubuntu just halt, without warning"
date: 2005-11-09
forum: Desktop Environments
---

### Post by omppa on 2005-11-09
Hi!

:confused: :confused:   I have quite anoying problem with ubuntu, it might just halts without any kind of warning, only thing wich help about this problem is reset button. What might be the problem?

my computer specs are

P3 600 MHz
320 MB memory
ati radeon 9250
100GB harddisk

---

### Post by schdefan on 2005-11-09
Take a look at the log file /var/log/syslog and see if you figure out some lines the causes the crash. Did you have any usb devidces connected?
schdefan

---

### Post by omppa on 2005-11-09
Well, i have to check this log file which you mention. 

Idon't have any usb-device connected into my computer.

Maybe this problem based in hardware? Overheating perhaphs...?

---

### Post by schdefan on 2005-11-09
does this happens every time when you turn on your computer  or when you start some particular programs?

---

### Post by omppa on 2005-11-09
After i install opera browser it appears first time, i thought that opera causes this problem but it appeared also when i use epiphany browsers.

---

### Post by schdefan on 2005-11-09
hard to say somethimg without any error messages. Did you find some entries in the log files?

---

### Post by omppa on 2005-11-09
i haven't check yet the log files, but i will tell you that did ai find anything from this log files.

---

### Post by schdefan on 2005-11-10
Perhaps you find some useful information in these links
[http://ubuntuforums.org/showthread.php?t=54930]("http://ubuntuforums.org/showthread.php?t=54930")
[http://bugzilla.ubuntu.com/show_bug.cgi?id=10579]("http://bugzilla.ubuntu.com/show_bug.cgi?id=10579")
schdefan

---

### Post by omppa on 2005-11-10
Here is little part of my ubuntu's syslog files:

Nov  9 23:06:32 localhost dhclient: DHCPREQUEST on eth0 to xxx.xxx.xxx.1 port 67
Nov  9 23:06:32 localhost dhclient: DHCPACK from xxx.xxx.xxx.1
Nov  9 23:06:32 localhost dhclient: bound to xxx.xxx.xxx.1 -- renewal in 1482 seconds.
Nov  9 23:14:47 localhost syslogd 1.4.1#16ubuntu6: restart.
Nov  9 23:14:47 localhost kernel: Inspecting /boot/System.map-2.6.10-5-386
Nov  9 23:14:47 localhost kernel: Loaded 27518 symbols from /boot/System.map-2.6.10-5-386.
Nov  9 23:14:47 localhost kernel: Symbols match kernel version 2.6.10.
Nov  9 23:14:47 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Nov  9 23:14:47 localhost kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Oct 10 11:15:41 UTC 2005
Nov  9 23:14:47 localhost kernel: BIOS-provided physical RAM map:
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 0000000000100000 - 0000000013ff0000 (usable)
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 0000000013ff0000 - 0000000013ff3000 (ACPI NVS)
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 0000000013ff3000 - 0000000014000000 (ACPI data)
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov  9 23:14:47 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Nov  9 23:14:47 localhost kernel: 319MB LOWMEM available.
Nov  9 23:14:47 localhost kernel: found SMP MP-table at 000f5b10
Nov  9 23:14:47 localhost kernel: On node 0 totalpages: 81904
Nov  9 23:14:47 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Nov  9 23:14:47 localhost kernel:   Normal zone: 77808 pages, LIFO batch:16
Nov  9 23:14:47 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Nov  9 23:14:47 localhost kernel: DMI 2.1 present.
Nov  9 23:14:47 localhost kernel: ACPI: RSDP (v000 GBT                                   ) @ 0x000f7190
Nov  9 23:14:47 localhost kernel: ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x13ff3000
Nov  9 23:14:47 localhost kernel: ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x13ff3040
Nov  9 23:14:47 localhost kernel: ACPI: MADT (v001 GBT             0x00000000  0x00000000) @ 0x13ff5440
Nov  9 23:14:47 localhost kernel: ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
Nov  9 23:14:47 localhost kernel: ACPI: PM-Timer IO Port: 0x4008
Nov  9 23:14:47 localhost kernel: ACPI: Local APIC address 0xfee00000
Nov  9 23:14:47 localhost kernel: ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov  9 23:14:47 localhost kernel: Processor #0 6:8 APIC version 17
Nov  9 23:14:47 localhost kernel: ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Nov  9 23:14:47 localhost kernel: ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov  9 23:14:47 localhost kernel: IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
Nov  9 23:14:47 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov  9 23:14:47 localhost kernel: ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
Nov  9 23:14:47 localhost kernel: ACPI: IRQ0 used by override.
Nov  9 23:14:47 localhost kernel: ACPI: IRQ2 used by override.
Nov  9 23:14:47 localhost kernel: ACPI: IRQ9 used by override.
Nov  9 23:14:47 localhost kernel: Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov  9 23:14:47 localhost kernel: Using ACPI (MADT) for SMP configuration information
Nov  9 23:14:47 localhost kernel: Built 1 zonelists
Nov  9 23:14:47 localhost kernel: Kernel command line: root=/dev/hdb1 ro quiet splash
Nov  9 23:14:47 localhost kernel: mapped APIC to ffffd000 (fee00000)
Nov  9 23:14:47 localhost kernel: mapped IOAPIC to ffffc000 (fec00000)
Nov  9 23:14:47 localhost kernel: Initializing CPU#0
Nov  9 23:14:47 localhost kernel: PID hash table entries: 2048 (order: 11, 32768 bytes)
Nov  9 23:14:47 localhost kernel: Detected 596.928 MHz processor.
Nov  9 23:14:47 localhost kernel: Using pmtmr for high-res timesource
Nov  9 23:14:47 localhost kernel: Console: colour VGA+ 80x25
Nov  9 23:14:47 localhost kernel: Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov  9 23:14:47 localhost kernel: Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov  9 23:14:47 localhost kernel: Memory: 317084k/327616k available (1437k kernel code, 9936k reserved, 753k data, 224k init, 0k highmem)
Nov  9 23:14:47 localhost kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov  9 23:14:47 localhost kernel: Calibrating delay loop... 1183.74 BogoMIPS (lpj=591872)
Nov  9 23:14:47 localhost kernel: Security Framework v1.0.0 initialized

Can someone tell me that can i find find reason for my ubuntu's halt from this logfile?

-Sami

---

### Post by schdefan on 2005-11-11
I am not very familiar with ACPI but you could try to disable it.
Edit the kernel line in file /boot/grub/menu.lst from 
> root=/dev/hdb1 ro quiet splash
to
> root=/dev/hdb1 ro quiet splash acpi=off
It is at the end of the file.

ACPI is not stable in Linux yet and some BIOS are also not fully supporting it. 
Maybe it is better in Breezy


schdefan

---

### Post by omppa on 2005-11-11
What does that ACPI makes or what it is? :confused: 

Well i'll have to try change this "root=/dev/hdb1 ro quiet splash" to root=/dev/hdb1 ro quiet splash acpi=off, and try that does my computer still halts.

-Sami

---

### Post by schdefan on 2005-11-11
Read here [ACPI]("http://en.wikipedia.org/wiki/ACPI")
Good luck
schdefan

---

### Post by omppa on 2005-11-11
Thanks a lot for that ACPI link. That clarifies to me a lot that ACPI problem ! :)

---

### Post by schdefan on 2005-11-11
no problems. Hope your system will work with disabled ACPI. Cause is kind of frustrating to find the errors. If that doe not work, boot into to recovery mode and see if your system freezes. If not than you have could  a problem with XServer or your graphic card.

schdefan

---

