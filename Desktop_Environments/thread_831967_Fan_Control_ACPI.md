---
title: "Fan Control ACPI"
date: 2008-06-17
forum: Desktop Environments
---

### Post by VMC on 2008-06-17
I noticed that my fan is almost all the time. In Windows this didn't happen, so I know their is fan-control. [Dell GX270] I guess it's referred to as ACPI.

I followed this path: [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI) which lead me to this

Fan Issues

These usually relate to the fan spinning too much or too fast. Another indication may be that the temperature remains high even when the fans are spinning.

   1. Determine if the system has ACPI-based fan control
          if /proc/acpi/fan is empty and /proc/acpi/thermal_zone/*/trip_points has no active trip points (those starting with "AC") then there is no ACPI-based fan control on your system
   2. If the system does have an ACPI-based fan control try booting with kernel parameter options listed above

What there referring to about "listed above" is turning ACPI off! The directories for acpi are empty.

How can I control the fan in Harty.

---

### Post by sdennie on 2008-06-17
You are saying there is nothing under /proc/acpi?  If so, are you booting with acpi=off?  A simple way to find out would be:

```

grep acpi /boot/grub/menu.lst

```

---

### Post by VMC on 2008-06-17
No I'm not running with ACPI=off. I just read that document and it suggested to use the commands above, but they didn't show how to turn it on. I'm guessing by it not being turned off, means it's turned on.

Here is my kernel output from menu.lst:
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d8533154-cef1-4cce-a823-9f3f74aab65b ro quiet splash vga=773

But the directories of "/proc/acpi/fan" and "/proc/acpi/thermal_zone/" are both empty.

---

### Post by sdennie on 2008-06-17
If those directories are empty it probably means that your BIOS is buggy or simply doesn't support those things.  One possible solution would be to flash your BIOS to a the newest version or, you could compile a custom DSDT, fix the possible errors and see if that solves the problem.  The latter is not trivial but, [http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems) looks like a good guide.

---

### Post by VMC on 2008-06-17
I'm reading the doc now. Thanks. I have the latest BIOS, and in Windows it works. I wonder how they used ACPI. I know it exists. I'll google more on Dell Optiplex for ACPI on Linux.

---

### Post by sdennie on 2008-06-17
Also, it's not uncommon to have /proc/acpi/fan be empty but, /proc/acpi/thermal_zone should probably have at least one thermal zone in it.

---

### Post by VMC on 2008-06-17
When I use acpi=force, I get the following. Notice the DSDT error. Maybe I do need to re-compile the kernel and add DSDT. That doesn't sound good. I haven't heard of anyone having heat issues with Optiplex though. The weird thing is, the reason I reported this is becasue I kept hearing the fan noise. Now no noise. Just power supply fan.

```
vmc@vmc-desktop:~$ dmesg|grep ACPI
[    0.000000]  BIOS-e820: 000000007fe70000 - 000000007fe72000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fe72000 - 000000007fe93000 (ACPI data)
[    0.000000] ACPI: RSDP signature @ 0xC00FEBA0 checksum 0
[    0.000000] ACPI: RSDP 000FEBA0, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD197, 0038 (r1 DELL    GX270          8 ASL        61)
[    0.000000] ACPI: FACP 000FD1CF, 0074 (r1 DELL    GX270          8 ASL        61)
[    0.000000] ACPI: DSDT FFFD31A7, 277F (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 7FE70000, 0040
[    0.000000] ACPI: SSDT FFFD5926, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD243, 006C (r1 DELL    GX270          8 ASL        61)
[    0.000000] ACPI: BOOT 000FD2AF, 0028 (r1 DELL    GX270          8 ASL        61)
[    0.000000] ACPI: ASF! 000FD2D7, 0067 (r16 DELL    GX270          8 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[   10.997157] ACPI: Core revision 20070126
[   11.009382] ACPI: **Looking for DSDT in initramfs... error, file /DSDT.aml not found**.
[   11.293339] ACPI: bus type pci registered
[   11.319838] ACPI: EC: Look up EC in DSDT
[   11.348522] ACPI: Interpreter enabled
[   11.348532] ACPI: (supports S0 S1 S3 S4 S5)
[   11.348558] ACPI: Using IOAPIC for interrupt routing
[   11.375181] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   11.375762] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   11.376177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   11.376657] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   11.488447] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   11.488765] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 15)
[   11.489079] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   11.489390] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   11.489699] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   11.490014] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   11.490327] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   11.490643] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 9 10 11 12 15)
[   11.490977] pnp: PnP ACPI init
[   11.490991] ACPI: bus type pnp registered
[   11.515146] pnp: PnP ACPI: found 9 devices
[   11.515153] ACPI: ACPI bus type pnp unregistered
[   11.515160] PnPBIOS: Disabled by ACPI PNP
[   11.515577] PCI: Using ACPI for IRQ routing
[   14.431375] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.535188] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   14.639013] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.742800] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
[   14.846678] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   14.970674] ACPI: PCI Interrupt 0000:01:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
[   15.287934] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   15.961466] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
[   31.265610] ACPI: Power Button (FF) [PWRF]
[   31.277594] ACPI: Power Button (CM) [VBTN]
[   33.321579] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
[   41.626539] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16

```

---

### Post by VMC on 2008-06-17
This problem has lead me far and wide. There is several people attaching this problem from different angles.

I'm only continuing here just in case someone else has a similar problem.

Here's one reference to dmesg that I have regarding "ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found "
If you do this from Terminal: dmesg|grep ACPI it shows up.

[http://ubuntuforums.org/showthread.php?t=629707&page=2](http://ubuntuforums.org/showthread.php?t=629707&page=2)
The above "fix" was for some to just turn it off! I guess if its out of sight, its out of mind.

I have a Dell Optiplix GX270. I found this very interesting link:
[http://www.linuxquestions.org/questions/linux-hardware-18/no-acpi-on-optiplex-gx240-605011/](http://www.linuxquestions.org/questions/linux-hardware-18/no-acpi-on-optiplex-gx240-605011/)

I have the exact same error when I tried to compile DSDT, BUT the above link may hold an answer. A guy there reported that the FAN is control by the BIOS and NOT the OS. Maybe I'm chasing wild horses here, but I still wonder why the DSTS Warning. Can't trace that one down.

---

