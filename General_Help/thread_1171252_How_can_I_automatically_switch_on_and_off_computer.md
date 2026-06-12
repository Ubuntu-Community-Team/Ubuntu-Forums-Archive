---
title: "How can I automatically switch on and off computer"
date: 2009-05-27
forum: General Help
---

### Post by sn0m on 2009-05-27
Hi guys
I've set up a desktop to use as a backup for my laptops using the almighty rsync, and last hurdle is how to set it up so it comes on once a week for couple of hours and then it goes back to sleep.
Thanks for help in advance.
Sokol

---

### Post by Dngrsone on 2009-05-27
There are two ways I can think of doing this (off the top of my head):  Wake on LAN or Scheduled Start.

Wake on LAN requires a motherboard (or add-in network card with cooperation form the motherboard) that will allow a signal from the local network to activate the computer.  If your motherboard has a built-in NIC, then look for Wake on LAN or other Events settings in the BIOS.  You could probably set up a cron job in your computer to wake the storage machine and then do the backup.

Scheduled Start is also a BIOS setting in the computer.  This tells the machine to turn on at certain times of day or on certain days.  You might be able to get the machine to turn itself on and run a script that does your archiving then turns off once the archiving is done.

---

### Post by tomsimmons on 2009-05-27
Well assuming it has a fairly standard BIOS you could could set up that up to start the machine up.

Shutting down, a CRON job?

A possible alternative...could you make do with suspend by CRON and if it's supported (someone else know?) wake up by a CRON?

I'm assuing your're on Linux?  If not the BIOS for start up still applies, and again you can schedule a shutdown - but I can't recall how.


Tom

---

### Post by perrti-y02 on 2009-05-27
To get it to turn off could you not add a line to the boot up script saying 

shutdown -P 12:57

so it boots at, say 9:15 and you know the backup will take FAR less that 3 hours 42 minutes and it then shuts down. Fairly clunky but I see no reason why it shouldn't work.

---

### Post by Aearenda on 2009-05-27
If your BIOS supports ACPI timer wakeups, you might be able to do something by following [this how-to]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake"). Even though it was written for Mythbuntu, it works for me using Ubuntu 8.04, using the following cron jobs:

```
## Wake up in 7 hours and 35 minutes = 7am
25 23 * * * echo "+00-00-00 07:35:00" > /proc/acpi/alarm

## Shut down at 11:50pm
50 23 * * * /sbin/shutdown -h -P now
```
I modified /etc/init.d/hwclock.sh as described in the how-to.

---

### Post by lavinog on 2009-05-28
I found this link [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
it seems newer kernels don't use /proc/acpi/alarm anymore but /sys/class/rtc/rtc0/wakealarm instead.

---

### Post by sn0m on 2009-05-28
Thanks for your help guys.
I was exploring the thread provided by Aearenda:
My bios support wake up from rtc alarm, and is in state S1, not sure what that means.
Back to ubuntu, output:
sn0m@sn0m-desktop:~$ dmesg|grep -i acpi
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  modified: 000000007ffc0000 - 000000007ffce000 (ACPI data)
[    0.000000]  modified: 000000007ffce000 - 000000007fff0000 (ACPI NVS)
[    0.000000] ACPI: RSDP 000FA120, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFC0000, 0038 (r1 010909 RSDT1525 20090109 MSFT       97)
[    0.000000] ACPI: FACP 7FFC0200, 0084 (r1 010909 FACP1525 20090109 MSFT       97)
[    0.000000] ACPI: DSDT 7FFC04A0, 4880 (r1  1ADKR 1ADKR017       17 INTL 20051117)
[    0.000000] ACPI: FACS 7FFCE000, 0040
[    0.000000] ACPI: APIC 7FFC0390, 0080 (r1 010909 APIC1525 20090109 MSFT       97)
[    0.000000] ACPI: MCFG 7FFC0410, 003C (r1 010909 OEMMCFG  20090109 MSFT       97)
[    0.000000] ACPI: WDRT 7FFC0450, 0047 (r1 010909 NV-WDRT  20090109 MSFT       97)
[    0.000000] ACPI: OEMB 7FFCE040, 0071 (r1 010909 OEMB1525 20090109 MSFT       97)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.005381] ACPI: Core revision 20080926
[    0.006493] ACPI: Checking initramfs for custom DSDT
[    0.336296] ACPI: bus type pci registered
[    0.336614] ACPI: EC: Look up EC in DSDT
[    0.344551] ACPI: Interpreter enabled
[    0.344553] ACPI: (supports S0 S1 S3 S4 S5)
[    0.344568] ACPI: Using IOAPIC for interrupt routing
[    0.348422] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.365071] ACPI: No dock devices found.
[    0.365119] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.366055] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.366250] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.366358] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.366436] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.366515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.371930] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.372128] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *11
[    0.372309] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *5
[    0.372488] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.372669] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
[    0.372847] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.373025] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.373206] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *10
[    0.373387] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.373569] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.373750] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.373931] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *5
[    0.374109] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.374291] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.374473] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *5
[    0.374654] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.374832] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *0, disabled.
[    0.375042] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.375131] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - E9, should be DC [20080926]
[    0.375145] ACPI: WMI: Mapper loaded
[    0.375210] PCI: Using ACPI for IRQ routing
[    0.400006] pnp: PnP ACPI init
[    0.400011] ACPI: bus type pnp registered
[    0.404242] pnp: PnP ACPI: found 14 devices
[    0.404243] ACPI: ACPI bus type pnp unregistered
[    0.910352] ACPI: Power Button (FF) [PWRF]
[    0.910393] ACPI: Power Button (CM) [PWRB]
[    0.910570] processor ACPI_CPU:00: registered as cooling_device0
[    0.910592] processor ACPI_CPU:01: registered as cooling_device1
[    0.942132] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    2.221275] ata3: nv_mode_filter: 0x739f&0x701f->0x701f, BIOS=0x7000 (0xc0c60000) ACPI=0x701f (60:20:0x15)
[    2.221278] ata3: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc0c60000) ACPI=0x3f01f (60:20:0x15)
[    2.347627] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    2.356933] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    2.461923] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    2.461993] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    2.630438] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    8.154889] ACPI: PCI Interrupt Link [LNED] enabled at IRQ 19
[    8.175164] parport_pc 00:07: reported by Plug and Play ACPI
[    8.652018] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 18
[    8.688201] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 23
[    8.731791] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 17
[    9.540410] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 16
sn0m@sn0m-desktop:~$ 
next

sn0m@sn0m-desktop:~$  find /proc/acpi/alarm
find: ‘/proc/acpi/alarm’: No such file or directory
sn0m@sn0m-desktop:~$ 

next
sn0m@sn0m-desktop:~$ ls /proc/acpi
ac_adapter  battery  button  dsdt  embedded_controller  event  fadt  fan  info  power_resource  processor  sleep  thermal_zone  video  wakeup


so one, there some sort of bug in bios in reg to linux then ther is no alarm in acpi, only wakeup. does that mean that I have to use wakeup as alarm? I have acpi support installed already.
Thanks for your help in advance
Sokol

---

### Post by lavinog on 2009-05-28
> **sn0m said:**
> 
find: ‘/proc/acpi/alarm’: No such file or directory


I guess you didn't read my post:
> it seems newer kernels don't use /proc/acpi/alarm anymore but /sys/class/rtc/rtc0/wakealarm instead.

---

