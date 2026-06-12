---
title: "ACPI: Looking for DSDT ... not found!"
date: 2006-08-10
forum: Desktop Environments
---

### Post by dcherryholmes on 2006-08-10
I found this message in /var/log/messages.... 

ACPI: Looking for DSDT ... not found!

Does anyone know what it means?  Is it a problem?

---

### Post by jetblack on 2006-08-10
The DSDT basically describes your system configuration for ACPI. Without it, you won't have ACPI support. If you don't need ACPI support then it's not a problem, but if you do then it is.

---

### Post by dcherryholmes on 2006-08-10
Thanks for the reply.  I'm using a laptop, so I certainly do need it.  Any ideas on what to look at next?  Maybe apt-cache search acpi and dpkg-reconfigure foo?

---

### Post by jetblack on 2006-08-10
Hoo boy. It's likely going to be more involved than that, unfortunately. Could you tell me what kind of laptop it is (make/model and all that)? It's been a little while since I wrangled with ACPI, but I might be able to help out a bit.

---

### Post by dcherryholmes on 2006-08-10
Yeah, the last time I messed with ACPI was when I was rolling my own on Gentoo (long since brain-dumped the details).  I'm running Dapper on a Thinkpad R52.  I'll keep looking myself (I'm not a total noob, I was just trying to take the easy way out) and post anything I find.

---

### Post by dcherryholmes on 2006-08-10
FYI, no error messages in /var/log/acpid

---

### Post by jetblack on 2006-08-10
> **dcherryholmes said:**
> Yeah, the last time I messed with ACPI was when I was rolling my own on Gentoo (long since brain-dumped the details).

Ah... did you happen to run across [this](http://forums.gentoo.org/viewtopic.php?t=122145)? ;)
It's a bit outdated, but may still be useful.

> **dcherryholmes said:**
>  I'm running Dapper on a Thinkpad R52.  I'll keep looking myself (I'm not a total noob, I was just trying to take the easy way out) and post anything I find.

Hrm - I always thought Thinkpads had pretty good support. There is a pretty [lengthy thread](http://ubuntuforums.org/showthread.php?t=186003) here about ACPI issues. [This post](http://ubuntuforums.org/showpost.php?p=1337116&postcount=146) seems to indicate a new kernel that might help out, but I haven't had time to actually read through the thread to make sure. Might be worth a look.

[This wiki](http://www.thinkwiki.org/wiki/How_to_control_fan_speed) focuses on fan speed, but the author claims to have succeeded in getting it to work on an R52. It may also have some good leads for you.

Good luck! I'll also let you know if I turn anything else up. Unfortunately, the acpi4linux [DSDT repository](http://acpi.sourceforge.net/dsdt/view.php?manufacturer=IBM) doesn't have fixed DSDTs for the R52.

---

### Post by jetblack on 2006-08-10
> **dcherryholmes said:**
> FYI, no error messages in /var/log/acpid

Does cat /proc/acpi/dsdt yield anything? Is there anything under /proc/acpi?

---

### Post by ymeng on 2006-10-07
I got the same error in my dmesg dump. Based on [http://bugzilla.kernel.org/show_bug.cgi?id=7089](http://bugzilla.kernel.org/show_bug.cgi?id=7089), this might be displayed incorrectly by another module.

I have an old sony desktop, motherboard P4B266LM is blacklisted. I added acpi=force with Ubuntu 6.06, but my power fan runs crazy constantly, see [http://ubuntuforums.org/showthread.php?p=1553685#8](http://ubuntuforums.org/showthread.php?p=1553685#8)

I followed [http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145) by "jetblack" (I hope it's the same jetblack) to fix the dsdt. When I disassembled and recompiled dsdt, I didn't get any errors. I have pasted below the dmesg dump and the 1st part of the dsdt. 

Does anyone know if the original dsdt come from the BIOS (Award BIOS, V102 [http://www.esupport.com/home.cfm](http://www.esupport.com/home.cfm)) or board vendor(ASUS)?

I can see in the BIOS setup, motherboard and CPU tempatures are monitored, so are CPU and power fan speeds. However, everyting under /proc/acpi is pretty much empty. Is there anyway I can tweak ACPI to control the fans? 

Any help is greatly appreciated. THX!!!

***************** demsg | grep -i acpi **************

[17179569.184000]  BIOS-e820: 000000000fffc000 - 000000000ffff000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000ffff000 - 0000000010000000 (ACPI NVS)
[17179569.184000] Warning: acpi=force overrules DMI blacklist: acpi=ht
[17179569.184000] ACPI: RSDP (v000 ASUS                                  ) @ 0x000f7400
[17179569.184000] ACPI: RSDT (v001 ASUS   P4B266LM 0x42302e31 MSFT 0x31313031) @ 0x0fffc000
[17179569.184000] ACPI: FADT (v001 ASUS   P4B266LM 0x42302e31 MSFT 0x31313031) @ 0x0fffc100
[17179569.184000] ACPI: BOOT (v001 ASUS   P4B266LM 0x42302e31 MSFT 0x31313031) @ 0x0fffc040
[17179569.184000] ACPI: MADT (v001 ASUS   P4B266LM 0x42302e31 MSFT 0x31313031) @ 0x0fffc080
[17179569.184000] ACPI: DSDT (v001   ASUS P4B266LM 0x00001000 MSFT 0x0100000b) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0xe408
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 22 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Kernel command line: root=/dev/hdb1 ro quiet splash acpi=force
[17179571.508000] ACPI: Looking for DSDT ... not found!
[17179571.656000] ACPI: bus type pci registered
[17179571.656000] ACPI: Subsystem revision 20051216
[17179571.660000] ACPI: Interpreter enabled
[17179571.660000] ACPI: Using IOAPIC for interrupt routing
[17179571.660000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179571.660000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[17179571.660000] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[17179571.660000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.660000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.660000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.664000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179571.664000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179571.664000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.664000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.672000] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[17179571.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.720000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[17179571.724000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[17179571.732000] pnp: PnP ACPI init
[17179571.736000] pnp: PnP ACPI: found 15 devices
[17179571.736000] PnPBIOS: Disabled by ACPI PNP
[17179571.736000] PCI: Using ACPI for IRQ routing
[17179572.172000] ACPI wakeup devices: 
[17179572.172000] ACPI: (supports S0 S1 S3 S4 S5)
[17179577.744000] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 177
[17179577.848000] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 185
[17179577.952000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179588.888000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 201
[17179588.900000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179589.140000] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 209
[17179589.264000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 217
[17179600.464000] ACPI: Power Button (FF) [PWRF]
[17179600.464000] ACPI: Power Button (CM) [PWRB]
[17179600.624000] ibm_acpi: ec object not found
[17179600.668000] pcc_acpi: loading...
[17179606.308000] apm: overridden by ACPI.
[17179733.016000] ACPI: PCI interrupt for device 0000:02:0d.0 disabled
[17179740.016000] NVRM: ACPI: unsupported event: 1
[17179740.016000] ACPI: PCI Interrupt 0000:02:0b.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179740.016000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> GSI 18 (level, low) -> IRQ 193
[17179743.248000] ACPI: PCI Interrupt 0000:02:0d.0[A] -> GSI 21 (level, low) -> IRQ 209
[17179745.608000] ACPI: Power Button (FF) [PWRF]
[17179745.608000] ACPI: Power Button (CM) [PWRB]

************** top part of dsdt.dsl ****************

/*
 * Intel ACPI Component Architecture
 * AML Disassembler version 20060912
 *
 * Disassembly of dsdt.dat, Fri Oct  6 23:36:10 2006
 *
 *
 * Original Table Header:
 *     Signature        "DSDT"
 *     Length           0x000023EB (9195)
 *     Revision         0x01
 *     OEM ID           "ASUS"
 *     OEM Table ID     "P4B266LM"
 *     OEM Revision     0x00001000 (4096)
 *     Creator ID       "MSFT"
 *     Creator Revision 0x0100000B (16777227)
 */
DefinitionBlock ("dsdt.aml", "DSDT", 1, "ASUS", "P4B266LM", 0x00001000)
{
    Scope (\_PR)
    {
        Processor (\_PR.CPU, 0x00, 0x00000000, 0x00) {}
    }

    OperationRegion (FSEG, SystemMemory, 0x000FDF00, 0x0100)
    Field (FSEG, AnyAcc, NoLock, Preserve)
    {
        ACPR,   32, 
        MMSZ,   16, 
        NPS2,   8, 
        STRF,   8, 
        HCUD,   8, 
        HCPI,   8, 
        HDUD,   8, 
        HDPI,   8, 
        HEUD,   8, 
        HEPI,   8, 
        HFUD,   8, 
        HFPI,   8, 
        VINT,   32, 
        FLG0,   8, 
        RTCS,   8
    }

    OperationRegion (NVSR, SystemMemory, ACPR, 0x0200)
    Field (NVSR, AnyAcc, NoLock, Preserve)
    {
        TRTY,   8, 
        SLPT,   8, 
        KPSW,   8, 
        MPSW,   8, 
        TRD0,   8, 
        TRD1,   8, 
        TRD2,   8, 
        TRD3,   8, 
                Offset (0x09), 
        INFB,   8, 
        INFO,   1600
    }

    Method (MIN, 2, NotSerialized)
    {
        If (LLess (Arg0, Arg1))
        {
            Return (Arg0)
        }
        Else
        {
            Return (Arg1)
        }
    }

    Method (SLEN, 1, NotSerialized)
    {
        Return (SizeOf (Arg0))
    }

    Method (S2BF, 1, Serialized)
    {
        Add (SLEN (Arg0), One, Local0)
        Name (BUFF, Buffer (Local0) {})
        Store (Arg0, BUFF)
        Return (BUFF)
    }

    Method (SCMP, 2, NotSerialized)
    {
        Store (S2BF (Arg0), Local0)
        Store (S2BF (Arg1), Local1)
        Store (Zero, Local4)
        Store (SLEN (Arg0), Local5)
        Store (SLEN (Arg1), Local6)
        Store (MIN (Local5, Local6), Local7)
        While (LLess (Local4, Local7))
        {
            Store (DerefOf (Index (Local0, Local4)), Local2)
            Store (DerefOf (Index (Local1, Local4)), Local3)
            If (LGreater (Local2, Local3))
            {
                Return (One)
            }
            Else
            {
                If (LLess (Local2, Local3))
                {
                    Return (Ones)
                }
            }

            Increment (Local4)
        }

        If (LLess (Local4, Local5))
        {
            Return (One)
        }
        Else
        {
            If (LLess (Local4, Local6))
            {
                Return (Ones)
            }
            Else
            {
                Return (Zero)
            }
        }
    }

---

### Post by Raoul Duke on 2006-10-24
Anything new on this issue? I am seeing the same thing on my new laptop
(Sony VIAO VGN-FE770G)...

dmesg|grep DSDT gives

[17179569.184000] ACPI: DSDT (v001   SONY       J3 0x20060921 PTL  0x20050228) @ 0x00000000
[17179573.908000] ACPI: Looking for DSDT ... not found!

I followed the acpi howto over at Gentoo. The dsdt extracted and compiled cleanly...what does it all mean? I have /proc/acpi, but with very limited functionality. sonypi and sony_acpi are both installed.
In particular I am trying to get function keys to work. In my (limited) understanding a non-buggy dsdt should give full acpi functionality?

---

### Post by rlklee on 2007-02-04
Bump.  I am having exactly the same problem on a sony vaio pcg-k45.  DSDT is not being recognized, though acpi seems to have limited functionality.  FN keys do not work, battery life is horribly short (maybe 45 minutes).   I've spent the last two hours searching and can't seem to find any solution.  I have however encountered *several* posts in which dmesg's are posted and contain the same DSDT not found message, usually in conjunction with ACPI problems, but the lack of DSDT recognition never comes up explicitly in the thread.  It makes me wonder whether this is a widespread laptop-bug that is going unnoticed.  

Does anybody have any current word on this?

---

### Post by TechZilla on 2007-10-22
ok i'm going to lay this out correctly.

the kenrnel is configured to look for the file "./DSDT.aml" if one is not found then instead of reading the file the kernel will read the acpi table from your machine.

a while ago almost everything had a severly broken ACPI and to get any decient support you had to compile a DSDT.aml file yourslef.  Which included fixing the asm errors.  So by not reading that file your kernel reads the DSDT from the computer,  If your computer has good support then don't worry about it.  It is not an error!!!

if you have no acpi support, and have knowlede that it is because your machine has a broken acpi table, and want to make your own DSDT.aml file then that is beyond this post.

but even if you do have no acpi support look elesewhere first, recompiling this file should be a last resort. (as it is not even close to simple, and requires some ASM knowledege)

---

