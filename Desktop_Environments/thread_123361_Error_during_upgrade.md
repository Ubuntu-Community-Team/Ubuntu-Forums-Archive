---
title: "Error during upgrade"
date: 2006-01-29
forum: Desktop Environments
---

### Post by durward on 2006-01-29
I have rebuilt an old computer:
**MB**:       Asus P2B ACPI rev 1011 with i440BX chipset, bus at 100; 
**CPU**:     Intel Pentium II-MMX 450 MHz; 
**RAM**:     192MB (128MB + 64MB, both PC100); 
**Video**:   Trident 3D Image 9750 AGP with 4MB VidRAM;
**NIC**:       Kingston KNE20T ISA
**FDD**:       Teac FD235HF
**IDE HDD**: WDC WD400BB-23DEA0 (40GB): default partitions for boot upon install
**CDROM**: Mitusumi FX320T 
**SCSI**:     Adaptec 2940U/UW bios 1.23
**Sound**:  Creative Sound Blaster Vibra16C
**4 SCSI HDDs**: 3xIBM-PSG-ST39175LW (9.1GB) and 1xIBM DGHS09U (9.1GB)
**PS**: Premier Performance Pro Model AP450DX

I installed Ubuntu Breezy Badger from a CD I burned; this is the third machine on which I have used this CD; the others work fine. The installation seems to be fine. Immediately after installation, there shows upgrades available. When I start the upgrades using the Software Updates, the problems begin.

At about 80% done, I get an error that stops the upgrade. This has happened three times now, each time I started with a cleaned harddisk (partitions deleted and reformatted). I even tried once to upgrade to the 686 version of Linux using the Synaptic Package Manager before downloading and installing the upgrades. The error is

    Setting up linux-image-2.6.12-10-386 (2.6.12.26) ...
    *** glibc detected *** malloc(): memory corruption: 0x08075190 ***

Each time before, I ran two different memory check programs, one from boot at GRUB, memory check program. There has been no memory problems found.

If I stop the installation (I have to so that I can proceed), then when I restart the machine, it stops during the boot with a similar error as shown above.

Can anyone tell me what is happening and how to fix it?

---

### Post by dcstar on 2006-01-29
[QUOTE=durward]I have rebuilt an old computer:
**MB**:       Asus P2B ACPI rev 1011 with i440BX chipset, bus at 100;
**CPU**:     Intel Pentium II-MMX 450 MHz;
**RAM**:     192MB (128MB + 64MB, both PC100);
......
If I stop the installation (I have to so that I can proceed), then when I restart the machine, it stops during the boot with a similar error as shown above.

Can anyone tell me what is happening and how to fix it?[/QUOTE]
I'd try removing the 64MB stick, and then see if the symptoms change.

BTW, is the CPU temperature ok, sometimes old CPU fans just don't work well enough when a CPU is stressed during an install process.

---

### Post by durward on 2006-01-30
The error occurs when:

1. 128MB stick
2. 64MB stick
3. 2x64MB sticks
4. 128MB + 64MB

I took out the Creative Sound Blaster Vibra16C and did selected upgrades, leaving out the linux lines. Then I upgraded, one at a time, the linux lines. It errored on:

    Unpacking replacement linux-386 ...
    Setting up linux-image-2.6.12-10-386 (2.6.12-10.26) ...
*** glibc detected *** malloc(): memory corruption: 0x0875190 ***

I giving up for tonight. I will start again sometime during the day, Monday.

---

