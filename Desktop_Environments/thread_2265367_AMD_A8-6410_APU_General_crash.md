---
title: "AMD A8-6410 APU: General crash"
date: 2015-02-14
forum: Desktop Environments
---

### Post by Freiklite on 2015-02-14
Hi,
The replay of "http://www.rai.tv/dl/RaiTV/programmi/media/ContentItem-e73cb512-bcd9-4d3c-95bd-8b8349565b3c.html" causes a pc crash.

After the general crash here's my .xsession-errors.old:> 
~$ cat .xsession-errors
Script for ibus started at run_im.


Here's a piece of dmesg.0 file:> 
[   16.878055] init: Error while reading from descriptor: Broken pipe
[   16.882832] init: failsafe main process (743) killed by TERM signal
[   18.541379] Bluetooth: Core ver 2.19
[   18.541413] NET: Registered protocol family 31
[   18.541417] Bluetooth: HCI device and connection manager initialized
[   18.541430] Bluetooth: HCI socket layer initialized
[   18.541433] Bluetooth: L2CAP socket layer initialized
[   18.541449] Bluetooth: SCO socket layer initialized
[   18.547152] Bluetooth: RFCOMM TTY layer initialized
[   18.547168] Bluetooth: RFCOMM socket layer initialized
[   18.547176] Bluetooth: RFCOMM ver 1.11
[   18.756921] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.756927] Bluetooth: BNEP filters: protocol multicast
[   18.756939] Bluetooth: BNEP socket layer initialized
[   18.922059] init: cups main process (888) killed by HUP signal
[   18.922080] init: cups main process ended, respawning
[   19.513107] systemd-logind[952]: New seat seat0.


Informations:
Hardware:```

dominique-satellite-c70d-b
    description: Ordinateur Bloc-notes
    produit: SATELLITE C70D-B (PSCLEE)
    fabriquant: TOSHIBA
    version: PSCLEE-00G009FR
    numéro de série: 9E058045U
    bits: 64 bits
    fonctionnalités: smbios-2.8 dmi-2.8 vsyscall32
    configuration: boot=normal chassis=notebook family=Arion 10AB sku=PSCLEE uuid=779BBB60-3C81-11E4-A8D6-008CFA86905A
  *-core
       description: Carte mère
       produit: Portable PC
       fabriquant: TOSHIBA
       identifiant matériel: 0
       version: MP
       numéro de série: 1
       emplacement: Base Board Chassis Location
     *-firmware
          description: BIOS
          fabriquant: Insyde Corp.
          identifiant matériel: 0
          version: 1.30
          date: 08/14/2014
          taille: 128KiB
          capacité: 8128KiB
          fonctionnalités: pci pnp upgrade shadowing cdboot bootselect edd int9keyboard int10video acpi usb smartbattery biosbootspecification netboot uefi


```
```

dominique@dominique-SATELLITE-C70D-B:/$ uname -a
Linux dominique-SATELLITE-C70D-B 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```
```

dominique@dominique-SATELLITE-C70D-B:/$ sudo lshw | grep ATI
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
             fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
dominique@dominique-SATELLITE-C70D-B:/$ sudo lshw | grep radeon
             configuration: driver=radeon latency=0
dominique@dominique-SATELLITE-C70D-B:/$ sudo lshw | grep R5
          produit: AMD A8-6410 APU with AMD Radeon R5 Graphics
          version: AMD A8-6410 APU with AMD Radeon R5 Graphics
             produit: Mullins [Radeon R4/R5 Graphics]

```
Firefox version: 34.0

Please help me. 
Thank you for your attention,
Bye.

---

### Post by Freiklite on 2015-02-15
hi, a piece of kern.log.1 at the very moment when the crash  happens:
```

 
Feb 14 18:12:27 debian kernel: imklog 5.8.11, log source = /proc/kmsg started.
Feb 14 18:12:27 debian kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 14 18:12:27 debian kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 14 18:12:27 debian kernel: [    0.000000] Linux version 3.2.0-4-amd64 (debian-kernel@lists.debian.org) (gcc version 4.6.3 (Debian 4.6.3-14) ) #1 SMP Debian 3.2.65-1+deb7u1
Feb 14 18:12:27 debian kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-4-amd64 root=UUID=1ba23965-7652-4f10-a52f-41bb82fd7619 ro quiet
Feb 14 18:12:27 debian kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000006e000 (usable)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 000000000006e000 - 0000000000070000 (ACPI NVS)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 0000000000070000 - 0000000000086000 (usable)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 0000000000086000 - 00000000000c0000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097c34000 (usable)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 0000000097c34000 - 000000009853c000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 000000009853c000 - 000000009f28f000 (usable)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 000000009f28f000 - 000000009f48f000 type 20
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 000000009f48f000 - 000000009fa8f000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 000000009fa8f000 - 000000009fb8f000 (ACPI NVS)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 000000009fb8f000 - 000000009fbff000 (ACPI data)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 000000009fbff000 - 000000009fc00000 (usable)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 000000009fc00000 - 00000000e0000000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 00000000f2800000 - 00000000f2900000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed81000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000021f000000 (usable)
Feb 14 18:12:27 debian kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 14 18:12:27 debian kernel: [    0.000000] EFI v2.31 by INSYDE Corp.
Feb 14 18:12:27 debian kernel: [    0.000000]  ACPI=0x9fbfe000  ACPI 2.0=0x9fbfe014  SMBIOS=0x9fa8ef98 
Feb 14 18:12:27 debian kernel: [    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006e000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem02: type=10, attr=0xf, range=[0x000000000006e000-0x0000000000070000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000086000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem04: type=0, attr=0xf, range=[0x0000000000086000-0x0000000000088000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem05: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x0000000000c54000) (11MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem07: type=7, attr=0xf, range=[0x0000000000c54000-0x0000000036a6a000) (862MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem08: type=2, attr=0xf, range=[0x0000000036a6a000-0x000000003752d000) (10MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem09: type=7, attr=0xf, range=[0x000000003752d000-0x000000006eddf000) (888MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem10: type=2, attr=0xf, range=[0x000000006eddf000-0x0000000095540000) (615MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x0000000095540000-0x0000000095560000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem12: type=7, attr=0xf, range=[0x0000000095560000-0x00000000967a8000) (18MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem13: type=2, attr=0xf, range=[0x00000000967a8000-0x0000000096895000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem14: type=7, attr=0xf, range=[0x0000000096895000-0x0000000096896000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem15: type=2, attr=0xf, range=[0x0000000096896000-0x0000000096897000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem16: type=7, attr=0xf, range=[0x0000000096897000-0x0000000096898000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem17: type=2, attr=0xf, range=[0x0000000096898000-0x000000009689d000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem18: type=7, attr=0xf, range=[0x000000009689d000-0x00000000968a1000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem19: type=2, attr=0xf, range=[0x00000000968a1000-0x00000000968a3000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem20: type=7, attr=0xf, range=[0x00000000968a3000-0x00000000968a5000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem21: type=2, attr=0xf, range=[0x00000000968a5000-0x00000000968a6000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem22: type=7, attr=0xf, range=[0x00000000968a6000-0x00000000968a7000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem23: type=2, attr=0xf, range=[0x00000000968a7000-0x00000000968a8000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem24: type=7, attr=0xf, range=[0x00000000968a8000-0x00000000968a9000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem25: type=2, attr=0xf, range=[0x00000000968a9000-0x00000000968aa000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem26: type=7, attr=0xf, range=[0x00000000968aa000-0x00000000968ac000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem27: type=2, attr=0xf, range=[0x00000000968ac000-0x0000000096996000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem28: type=4, attr=0xf, range=[0x0000000096996000-0x0000000097c34000) (18MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem29: type=0, attr=0xf, range=[0x0000000097c34000-0x000000009853c000) (9MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem30: type=2, attr=0xf, range=[0x000000009853c000-0x000000009853f000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem31: type=7, attr=0xf, range=[0x000000009853f000-0x000000009861c000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem32: type=1, attr=0xf, range=[0x000000009861c000-0x000000009873f000) (1MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem33: type=7, attr=0xf, range=[0x000000009873f000-0x000000009bb84000) (52MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem34: type=4, attr=0xf, range=[0x000000009bb84000-0x000000009bb9b000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem35: type=7, attr=0xf, range=[0x000000009bb9b000-0x000000009bbb9000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem36: type=4, attr=0xf, range=[0x000000009bbb9000-0x000000009bbd7000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem37: type=7, attr=0xf, range=[0x000000009bbd7000-0x000000009bbd8000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem38: type=4, attr=0xf, range=[0x000000009bbd8000-0x000000009ca0e000) (14MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem39: type=7, attr=0xf, range=[0x000000009ca0e000-0x000000009ca11000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem40: type=4, attr=0xf, range=[0x000000009ca11000-0x000000009ca19000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem41: type=7, attr=0xf, range=[0x000000009ca19000-0x000000009ca1c000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem42: type=4, attr=0xf, range=[0x000000009ca1c000-0x000000009ec8f000) (34MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem43: type=7, attr=0xf, range=[0x000000009ec8f000-0x000000009ee36000) (1MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem44: type=2, attr=0xf, range=[0x000000009ee36000-0x000000009ee40000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem45: type=3, attr=0xf, range=[0x000000009ee40000-0x000000009f28f000) (4MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem46: type=5, attr=0x800000000000000f, range=[0x000000009f28f000-0x000000009f48f000) (2MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem47: type=6, attr=0x800000000000000f, range=[0x000000009f48f000-0x000000009f68f000) (2MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem48: type=0, attr=0xf, range=[0x000000009f68f000-0x000000009fa8f000) (4MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem49: type=10, attr=0xf, range=[0x000000009fa8f000-0x000000009fb8f000) (1MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem50: type=9, attr=0xf, range=[0x000000009fb8f000-0x000000009fbff000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem51: type=4, attr=0xf, range=[0x000000009fbff000-0x000000009fc00000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem52: type=7, attr=0xf, range=[0x0000000100000000-0x000000021f000000) (4592MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem53: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem54: type=0, attr=0x0, range=[0x000000009fc00000-0x00000000e0000000) (1028MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem55: type=11, attr=0x8000000000000000, range=[0x00000000f2800000-0x00000000f2900000) (1MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem56: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem57: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec02000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem58: type=11, attr=0x8000000000000001, range=[0x00000000fec10000-0x00000000fec11000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem59: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed81000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem60: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
Feb 14 18:12:27 debian kernel: [    0.000000] EFI: mem61: type=11, attr=0x8000000000000000, range=[0x00000000ff800000-0x0000000100000000) (8MB)
Feb 14 18:12:27 debian kernel: [    0.000000] SMBIOS 2.8 present.
Feb 14 18:12:27 debian kernel: [    0.000000] DMI: TOSHIBA SATELLITE C70D-B/Portable PC, BIOS 1.30 08/14/2014
Feb 14 18:12:27 debian kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Feb 14 18:12:27 debian kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Feb 14 18:12:27 debian kernel: [    0.000000] No AGP bridge found
Feb 14 18:12:27 debian kernel: [    0.000000] last_pfn = 0x21f000 max_arch_pfn = 0x400000000
Feb 14 18:12:27 debian kernel: [    0.000000] MTRR default type: uncachable
Feb 14 18:12:27 debian kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 14 18:12:27 debian kernel: [    0.000000]   00000-9FFFF write-back
Feb 14 18:12:27 debian kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 14 18:12:27 debian kernel: [    0.000000]   C0000-FFFFF write-through
Feb 14 18:12:27 debian kernel: [    0.000000] MTRR variable ranges enabled:
Feb 14 18:12:27 debian kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Feb 14 18:12:27 debian kernel: [    0.000000]   1 base 0080000000 mask FFE0000000 write-back
Feb 14 18:12:27 debian kernel: [    0.000000]   2 base 009FB78000 mask FFFFFFF000 uncachable
Feb 14 18:12:27 debian kernel: [    0.000000]   3 base 00FF800000 mask FFFF800000 write-protect
Feb 14 18:12:27 debian kernel: [    0.000000]   4 disabled
Feb 14 18:12:27 debian kernel: [    0.000000]   5 disabled
Feb 14 18:12:27 debian kernel: [    0.000000]   6 disabled
Feb 14 18:12:27 debian kernel: [    0.000000]   7 disabled
Feb 14 18:12:27 debian kernel: [    0.000000] TOM2: 000000021f000000 aka 8688M
Feb 14 18:12:27 debian kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 14 18:12:27 debian kernel: [    0.000000] last_pfn = 0x9fc00 max_arch_pfn = 0x400000000
Feb 14 18:12:27 debian kernel: [    0.000000] initial memory mapped : 0 - 20000000
Feb 14 18:12:27 debian kernel: [    0.000000] Base memory trampoline at [ffff88000007d000] 7d000 size 20480
Feb 14 18:12:27 debian kernel: [    0.000000] Using GB pages for direct mapping
Feb 14 18:12:27 debian kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000009fc00000
Feb 14 18:12:27 debian kernel: [    0.000000]  0000000000 - 0080000000 page 1G
Feb 14 18:12:27 debian kernel: [    0.000000]  0080000000 - 009fc00000 page 2M
Feb 14 18:12:27 debian kernel: [    0.000000] kernel direct mapping tables up to 9fc00000 @ 1fffe000-20000000
Feb 14 18:12:27 debian kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000021f000000
Feb 14 18:12:27 debian kernel: [    0.000000]  0100000000 - 0200000000 page 1G
Feb 14 18:12:27 debian kernel: [    0.000000]  0200000000 - 021f000000 page 2M
Feb 14 18:12:27 debian kernel: [    0.000000] kernel direct mapping tables up to 21f000000 @ 9ee3e000-9ee40000
Feb 14 18:12:27 debian kernel: [    0.000000] RAMDISK: 36a6a000 - 3752d000
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: RSDP 000000009fbfe014 00024 (v02 TOSINV)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: XSDT 000000009fbc7188 000D4 (v01 TOSINV TOSINV00 00000001      01000013)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: FACP 000000009fbfc000 0010C (v05 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: DSDT 000000009fbf2000 05F3F (v01 TOSINV TOSINV00 F0000000 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: FACS 000000009fb2f000 00040
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: UEFI 000000009fbfd000 00236 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: HPET 000000009fbfb000 00038 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: APIC 000000009fbfa000 00090 (v03 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: MCFG 000000009fbf9000 0003C (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: ASF! 000000009fbf8000 000A5 (v32 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: BOOT 000000009fbf1000 00028 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SLIC 000000009fbf0000 00176 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: FPDT 000000009fbee000 00044 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: MSDM 000000009fbed000 00055 (v03 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbe6000 06D71 (v01 TOSINV   TsbOdm 00001000 INTL 20120215)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbe5000 00CB0 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbe0000 0487A (v02 TOSINV TOSINV00 00000002 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: VFCT 000000009fbd1000 0EC84 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbd0000 0085A (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbcf000 00418 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbcd000 01309 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbcc000 0008C (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbca000 01138 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: SSDT 000000009fbc8000 00FB4 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: WPBT 000000009fbbe000 00038 (v01 TOSINV TOSINV00 00000001 ABTW 20120402)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: BGRT 000000009fbc9000 00038 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 14 18:12:27 debian kernel: [    0.000000] No NUMA configuration found
Feb 14 18:12:27 debian kernel: [    0.000000] Faking a node at 0000000000000000-000000021f000000
Feb 14 18:12:27 debian kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000021f000000
Feb 14 18:12:27 debian kernel: [    0.000000]   NODE_DATA [000000021effb000 - 000000021effffff]
Feb 14 18:12:27 debian kernel: [    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880217600000-ffff88021d9fffff] on node 0
Feb 14 18:12:27 debian kernel: [    0.000000] Zone PFN ranges:
Feb 14 18:12:27 debian kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Feb 14 18:12:27 debian kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Feb 14 18:12:27 debian kernel: [    0.000000]   Normal   0x00100000 -> 0x0021f000
Feb 14 18:12:27 debian kernel: [    0.000000] Movable zone start PFN for each node
Feb 14 18:12:27 debian kernel: [    0.000000] early_node_map[6] active PFN ranges
Feb 14 18:12:27 debian kernel: [    0.000000]     0: 0x00000010 -> 0x0000006e
Feb 14 18:12:27 debian kernel: [    0.000000]     0: 0x00000070 -> 0x00000086
Feb 14 18:12:27 debian kernel: [    0.000000]     0: 0x00000100 -> 0x00097c34
Feb 14 18:12:27 debian kernel: [    0.000000]     0: 0x0009853c -> 0x0009f28f
Feb 14 18:12:27 debian kernel: [    0.000000]     0: 0x0009fbff -> 0x0009fc00
Feb 14 18:12:27 debian kernel: [    0.000000]     0: 0x00100000 -> 0x0021f000
Feb 14 18:12:27 debian kernel: [    0.000000] On node 0 totalpages: 1825020
Feb 14 18:12:27 debian kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Feb 14 18:12:27 debian kernel: [    0.000000]   DMA zone: 6 pages reserved
Feb 14 18:12:27 debian kernel: [    0.000000]   DMA zone: 3894 pages, LIFO batch:0
Feb 14 18:12:27 debian kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Feb 14 18:12:27 debian kernel: [    0.000000]   DMA32 zone: 631232 pages, LIFO batch:31
Feb 14 18:12:27 debian kernel: [    0.000000]   Normal zone: 16072 pages used for memmap
Feb 14 18:12:27 debian kernel: [    0.000000]   Normal zone: 1159480 pages, LIFO batch:31
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Feb 14 18:12:27 debian kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec01000] gsi_base[24])
Feb 14 18:12:27 debian kernel: [    0.000000] IOAPIC[1]: apic_id 5, version 33, address 0xfec01000, GSI 24-55
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 14 18:12:27 debian kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 14 18:12:27 debian kernel: [    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
Feb 14 18:12:27 debian kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Feb 14 18:12:27 debian kernel: [    0.000000] nr_irqs_gsi: 72
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 000000000006e000 - 0000000000070000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 0000000000086000 - 00000000000c0000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 0000000097c34000 - 000000009853c000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009f28f000 - 000000009f48f000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009f48f000 - 000000009fa8f000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009fa8f000 - 000000009fb8f000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009fb8f000 - 000000009fbff000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009fc00000 - 00000000e0000000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f2800000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000f2800000 - 00000000f2900000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000f2900000 - 00000000f8000000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec02000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fec02000 - 00000000fec10000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fed80000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed81000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fed81000 - 00000000fee00000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff800000
Feb 14 18:12:27 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000ff800000 - 0000000100000000
Feb 14 18:12:27 debian kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:12800000)
Feb 14 18:12:27 debian kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 14 18:12:27 debian kernel: [    0.000000] setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:4 nr_node_ids:1
Feb 14 18:12:27 debian kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021ec00000 s78848 r8192 d23552 u524288
Feb 14 18:12:27 debian kernel: [    0.000000] pcpu-alloc: s78848 r8192 d23552 u524288 alloc=1*2097152
Feb 14 18:12:27 debian kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Feb 14 18:12:27 debian kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1794606
Feb 14 18:12:27 debian kernel: [    0.000000] Policy zone: Normal
Feb 14 18:12:27 debian kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-4-amd64 root=UUID=1ba23965-7652-4f10-a52f-41bb82fd7619 ro quiet
Feb 14 18:12:27 debian kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb 14 18:12:27 debian kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Feb 14 18:12:27 debian kernel: [    0.000000] Checking aperture...
Feb 14 18:12:27 debian kernel: [    0.000000] No AGP bridge found
Feb 14 18:12:27 debian kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Feb 14 18:12:27 debian kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Feb 14 18:12:27 debian kernel: [    0.000000] Memory: 7037964k/8896512k available (3433k kernel code, 1596432k absent, 262116k reserved, 3305k data, 576k init)
Feb 14 18:12:27 debian kernel: [    0.000000] Hierarchical RCU implementation.
Feb 14 18:12:27 debian kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Feb 14 18:12:27 debian kernel: [    0.000000] NR_IRQS:33024 nr_irqs:1024 16
Feb 14 18:12:27 debian kernel: [    0.000000] Console: colour dummy device 80x25
Feb 14 18:12:27 debian kernel: [    0.000000] console [tty0] enabled
Feb 14 18:12:27 debian kernel: [    0.000000] hpet clockevent registered
Feb 14 18:12:27 debian kernel: [    0.000000] Fast TSC calibration using PIT
Feb 14 18:12:27 debian kernel: [    0.000000] Detected 1996.543 MHz processor.
Feb 14 18:12:27 debian kernel: [    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3993.08 BogoMIPS (lpj=7986172)
Feb 14 18:12:27 debian kernel: [    0.004012] pid_max: default: 32768 minimum: 301
Feb 14 18:12:27 debian kernel: [    0.028133] Security Framework initialized
Feb 14 18:12:27 debian kernel: [    0.028151] AppArmor: AppArmor disabled by boot time parameter
Feb 14 18:12:27 debian kernel: [    0.032551] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Feb 14 18:12:27 debian kernel: [    0.037417] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Feb 14 18:12:27 debian kernel: [    0.039882] Mount-cache hash table entries: 256
Feb 14 18:12:27 debian kernel: [    0.040154] Initializing cgroup subsys cpuacct
Feb 14 18:12:27 debian kernel: [    0.040161] Initializing cgroup subsys memory
Feb 14 18:12:27 debian kernel: [    0.040182] Initializing cgroup subsys devices
Feb 14 18:12:27 debian kernel: [    0.040185] Initializing cgroup subsys freezer
Feb 14 18:12:27 debian kernel: [    0.040189] Initializing cgroup subsys net_cls
Feb 14 18:12:27 debian kernel: [    0.040192] Initializing cgroup subsys blkio
Feb 14 18:12:27 debian kernel: [    0.040204] Initializing cgroup subsys perf_event
Feb 14 18:12:27 debian kernel: [    0.040255] tseg: 009fc00000
Feb 14 18:12:27 debian kernel: [    0.040258] CPU: Physical Processor ID: 0
Feb 14 18:12:27 debian kernel: [    0.040260] CPU: Processor Core ID: 0
Feb 14 18:12:27 debian kernel: [    0.049083] mce: CPU supports 6 MCE banks
Feb 14 18:12:27 debian kernel: [    0.049719] ACPI: Core revision 20110623
Feb 14 18:12:27 debian kernel: [    0.068639] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 14 18:12:27 debian kernel: [    0.108345] CPU0: AMD A8-6410 APU with AMD Radeon R5 Graphics     stepping 01
Feb 14 18:12:27 debian kernel: [    0.112006] Performance Events: AMD PMU driver.
Feb 14 18:12:27 debian kernel: [    0.112006] ... version:                0
Feb 14 18:12:27 debian kernel: [    0.112006] ... bit width:              48
Feb 14 18:12:27 debian kernel: [    0.112006] ... generic registers:      4
Feb 14 18:12:27 debian kernel: [    0.112006] ... value mask:             0000ffffffffffff
Feb 14 18:12:27 debian kernel: [    0.112006] ... max period:             00007fffffffffff
Feb 14 18:12:27 debian kernel: [    0.112006] ... fixed-purpose events:   0
Feb 14 18:12:27 debian kernel: [    0.112006] ... event mask:             000000000000000f
Feb 14 18:12:27 debian kernel: [    0.112006] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 18:12:27 debian kernel: [    0.112006] Booting Node   0, Processors  #1
Feb 14 18:12:27 debian kernel: [    0.112006] smpboot cpu 1: start_ip = 7d000
Feb 14 18:12:27 debian kernel: [    0.208080] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 18:12:27 debian kernel: [    0.208336]  #2
Feb 14 18:12:27 debian kernel: [    0.208338] smpboot cpu 2: start_ip = 7d000
Feb 14 18:12:27 debian kernel: [    0.312092] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 18:12:27 debian kernel: [    0.312344]  #3 Ok.
Feb 14 18:12:27 debian kernel: [    0.312346] smpboot cpu 3: start_ip = 7d000
Feb 14 18:12:27 debian kernel: [    0.416100] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 18:12:27 debian kernel: [    0.416187] Brought up 4 CPUs
Feb 14 18:12:27 debian kernel: [    0.416190] Total of 4 processors activated (15969.64 BogoMIPS).
Feb 14 18:12:27 debian kernel: [    0.417492] devtmpfs: initialized
Feb 14 18:12:27 debian kernel: [    0.422357] PM: Registering ACPI NVS region at 6e000 (8192 bytes)
Feb 14 18:12:27 debian kernel: [    0.422357] PM: Registering ACPI NVS region at 9fa8f000 (1048576 bytes)
Feb 14 18:12:27 debian kernel: [    0.422357] print_constraints: dummy: 
Feb 14 18:12:27 debian kernel: [    0.422357] NET: Registered protocol family 16
Feb 14 18:12:27 debian kernel: [    0.422357] Extended Config Space enabled on 0 nodes
Feb 14 18:12:27 debian kernel: [    0.422357] ACPI: bus type pci registered
Feb 14 18:12:27 debian kernel: [    0.422357] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Feb 14 18:12:27 debian kernel: [    0.422357] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Feb 14 18:12:27 debian kernel: [    0.428817] PCI: Using configuration type 1 for base access
Feb 14 18:12:27 debian kernel: [    0.429902] bio: create slab <bio-0> at 0
Feb 14 18:12:27 debian kernel: [    0.429902] ACPI: Added _OSI(Module Device)
Feb 14 18:12:27 debian kernel: [    0.429902] ACPI: Added _OSI(Processor Device)
Feb 14 18:12:27 debian kernel: [    0.429902] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb 14 18:12:27 debian kernel: [    0.429902] ACPI: Added _OSI(Processor Aggregator Device)
Feb 14 18:12:27 debian kernel: [    0.432442] ACPI: EC: Look up EC in DSDT
Feb 14 18:12:27 debian kernel: [    0.434758] ACPI: Executed 1 blocks of module-level executable AML code
Feb 14 18:12:27 debian kernel: [    0.456360] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Feb 14 18:12:27 debian kernel: [    0.614327] ACPI: Interpreter enabled
Feb 14 18:12:27 debian kernel: [    0.614336] ACPI: (supports S0 S3 S4 S5)
Feb 14 18:12:27 debian kernel: [    0.614368] ACPI: Using IOAPIC for interrupt routing
Feb 14 18:12:27 debian kernel: [    0.778874] ACPI: Power Resource [PFA1] (off)
Feb 14 18:12:27 debian kernel: [    0.828249] ACPI: No dock devices found.
Feb 14 18:12:27 debian kernel: [    0.828249] HEST: Table not found.
Feb 14 18:12:27 debian kernel: [    0.828249] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Feb 14 18:12:27 debian kernel: [    0.856250] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Feb 14 18:12:27 debian kernel: [    0.900215] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Feb 14 18:12:27 debian kernel: [    0.900220] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Feb 14 18:12:27 debian kernel: [    0.900223] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Feb 14 18:12:27 debian kernel: [    0.900226] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
Feb 14 18:12:27 debian kernel: [    0.900229] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
Feb 14 18:12:27 debian kernel: [    0.900232] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
Feb 14 18:12:27 debian kernel: [    0.900234] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
Feb 14 18:12:27 debian kernel: [    0.900237] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Feb 14 18:12:27 debian kernel: [    0.900240] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Feb 14 18:12:27 debian kernel: [    0.900246] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Feb 14 18:12:27 debian kernel: [    0.900248] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Feb 14 18:12:27 debian kernel: [    0.900251] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Feb 14 18:12:27 debian kernel: [    0.900254] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Feb 14 18:12:27 debian kernel: [    0.900256] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
Feb 14 18:12:27 debian kernel: [    0.900259] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
Feb 14 18:12:27 debian kernel: [    0.900262] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xf7ffffff]
Feb 14 18:12:27 debian kernel: [    0.900264] pci_root PNP0A08:00: host bridge window [mem 0xfc000000-0xfed3ffff]
Feb 14 18:12:27 debian kernel: [    0.900267] pci_root PNP0A08:00: host bridge window [mem 0xfed45000-0xffffffff]
Feb 14 18:12:27 debian kernel: [    0.900289] pci 0000:00:00.0: [1022:1566] type 0 class 0x000600
Feb 14 18:12:27 debian kernel: [    0.900340] pci 0000:00:01.0: [1002:9851] type 0 class 0x000300
Feb 14 18:12:27 debian kernel: [    0.900352] pci 0000:00:01.0: reg 10: [mem 0xe0000000-0xefffffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.900362] pci 0000:00:01.0: reg 18: [mem 0xf2000000-0xf27fffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.900368] pci 0000:00:01.0: reg 20: [io  0x3000-0x30ff]
Feb 14 18:12:27 debian kernel: [    0.900375] pci 0000:00:01.0: reg 24: [mem 0xf2c00000-0xf2c3ffff]
Feb 14 18:12:27 debian kernel: [    0.900381] pci 0000:00:01.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Feb 14 18:12:27 debian kernel: [    0.900413] pci 0000:00:01.0: supports D1 D2
Feb 14 18:12:27 debian kernel: [    0.900416] pci 0000:00:01.0: PME# supported from D1 D2 D3hot
Feb 14 18:12:27 debian kernel: [    0.900440] pci 0000:00:01.1: [1002:9840] type 0 class 0x000403
Feb 14 18:12:27 debian kernel: [    0.900452] pci 0000:00:01.1: reg 10: [mem 0xf2c60000-0xf2c63fff 64bit]
Feb 14 18:12:27 debian kernel: [    0.900502] pci 0000:00:01.1: supports D1 D2
Feb 14 18:12:27 debian kernel: [    0.900522] pci 0000:00:02.0: [1022:156b] type 0 class 0x000600
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:02.2: [1022:1439] type 1 class 0x000604
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:02.2: PME# supported from D0 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:02.3: [1022:1439] type 1 class 0x000604
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:02.3: PME# supported from D0 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:02.4: [1022:1439] type 1 class 0x000604
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:02.4: PME# supported from D0 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:08.0: [1022:1537] type 0 class 0x001080
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:08.0: reg 10: [mem 0xf2c40000-0xf2c5ffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:08.0: reg 18: [mem 0xf2900000-0xf29fffff]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:08.0: reg 1c: [mem 0xf2c6f000-0xf2c6ffff]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:08.0: reg 24: [mem 0xf2c6a000-0xf2c6bfff]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:10.0: [1022:7814] type 0 class 0x000c03
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:10.0: reg 10: [mem 0xf2c68000-0xf2c69fff 64bit]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:11.0: [1022:7801] type 0 class 0x000106
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:11.0: reg 10: [io  0x3118-0x311f]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:11.0: reg 14: [io  0x3124-0x3127]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:11.0: reg 18: [io  0x3110-0x3117]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:11.0: reg 1c: [io  0x3120-0x3123]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:11.0: reg 20: [io  0x3100-0x310f]
Feb 14 18:12:27 debian kernel: [    0.900556] pci 0000:00:11.0: reg 24: [mem 0xf2c6e000-0xf2c6e3ff]
Feb 14 18:12:27 debian kernel: [    0.900575] pci 0000:00:11.0: PME# supported from D3hot
Feb 14 18:12:27 debian kernel: [    0.900600] pci 0000:00:12.0: [1022:7808] type 0 class 0x000c03
Feb 14 18:12:27 debian kernel: [    0.900615] pci 0000:00:12.0: reg 10: [mem 0xf2c6d000-0xf2c6d0ff]
Feb 14 18:12:27 debian kernel: [    0.900677] pci 0000:00:12.0: supports D1 D2
Feb 14 18:12:27 debian kernel: [    0.900680] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.900701] pci 0000:00:13.0: [1022:7808] type 0 class 0x000c03
Feb 14 18:12:27 debian kernel: [    0.900716] pci 0000:00:13.0: reg 10: [mem 0xf2c6c000-0xf2c6c0ff]
Feb 14 18:12:27 debian kernel: [    0.900778] pci 0000:00:13.0: supports D1 D2
Feb 14 18:12:27 debian kernel: [    0.900780] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.900797] pci 0000:00:14.0: [1022:780b] type 0 class 0x000c05
Feb 14 18:12:27 debian kernel: [    0.900859] pci 0000:00:14.2: [1022:780d] type 0 class 0x000403
Feb 14 18:12:27 debian kernel: [    0.900878] pci 0000:00:14.2: reg 10: [mem 0xf2c64000-0xf2c67fff 64bit]
Feb 14 18:12:27 debian kernel: [    0.900935] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.900952] pci 0000:00:14.3: [1022:780e] type 0 class 0x000601
Feb 14 18:12:27 debian kernel: [    0.901021] pci 0000:00:18.0: [1022:1580] type 0 class 0x000600
Feb 14 18:12:27 debian kernel: [    0.901044] pci 0000:00:18.1: [1022:1581] type 0 class 0x000600
Feb 14 18:12:27 debian kernel: [    0.901065] pci 0000:00:18.2: [1022:1582] type 0 class 0x000600
Feb 14 18:12:27 debian kernel: [    0.901086] pci 0000:00:18.3: [1022:1583] type 0 class 0x000600
Feb 14 18:12:27 debian kernel: [    0.901112] pci 0000:00:18.4: [1022:1584] type 0 class 0x000600
Feb 14 18:12:27 debian kernel: [    0.901133] pci 0000:00:18.5: [1022:1585] type 0 class 0x000600
Feb 14 18:12:27 debian kernel: [    0.901212] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
Feb 14 18:12:27 debian kernel: [    0.901227] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
Feb 14 18:12:27 debian kernel: [    0.901251] pci 0000:01:00.0: reg 18: [mem 0xf1000000-0xf1000fff 64bit]
Feb 14 18:12:27 debian kernel: [    0.901267] pci 0000:01:00.0: reg 20: [mem 0xf0000000-0xf0003fff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.901331] pci 0000:01:00.0: supports D1 D2
Feb 14 18:12:27 debian kernel: [    0.901334] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.908128] pci 0000:00:02.2: PCI bridge to [bus 01-04]
Feb 14 18:12:27 debian kernel: [    0.908137] pci 0000:00:02.2:   bridge window [io  0x2000-0x2fff]
Feb 14 18:12:27 debian kernel: [    0.908141] pci 0000:00:02.2:   bridge window [mem 0xf1000000-0xf1ffffff]
Feb 14 18:12:27 debian kernel: [    0.908147] pci 0000:00:02.2:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.908242] pci 0000:05:00.0: [14e4:4365] type 0 class 0x000280
Feb 14 18:12:27 debian kernel: [    0.908267] pci 0000:05:00.0: reg 10: [mem 0xf2b00000-0xf2b07fff 64bit]
Feb 14 18:12:27 debian kernel: [    0.908378] pci 0000:05:00.0: supports D1 D2
Feb 14 18:12:27 debian kernel: [    0.908381] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
Feb 14 18:12:27 debian kernel: [    0.916119] pci 0000:00:02.3: PCI bridge to [bus 05-05]
Feb 14 18:12:27 debian kernel: [    0.916130] pci 0000:00:02.3:   bridge window [mem 0xf2b00000-0xf2bfffff]
Feb 14 18:12:27 debian kernel: [    0.916206] pci 0000:06:00.0: [10ec:5229] type 0 class 0x00ff00
Feb 14 18:12:27 debian kernel: [    0.916225] pci 0000:06:00.0: reg 10: [mem 0xf2a00000-0xf2a00fff]
Feb 14 18:12:27 debian kernel: [    0.916335] pci 0000:06:00.0: supports D1 D2
Feb 14 18:12:27 debian kernel: [    0.916338] pci 0000:06:00.0: PME# supported from D1 D2 D3hot
Feb 14 18:12:27 debian kernel: [    0.924126] pci 0000:00:02.4: PCI bridge to [bus 06-06]
Feb 14 18:12:27 debian kernel: [    0.924137] pci 0000:00:02.4:   bridge window [mem 0xf2a00000-0xf2afffff]
Feb 14 18:12:27 debian kernel: [    0.924169] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 14 18:12:27 debian kernel: [    0.924374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GPP0._PRT]
Feb 14 18:12:27 debian kernel: [    0.924441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GPP1._PRT]
Feb 14 18:12:27 debian kernel: [    0.924514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GPP2._PRT]
Feb 14 18:12:27 debian kernel: [    0.924636]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Feb 14 18:12:27 debian kernel: [    0.924641]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 14 18:12:27 debian kernel: [    0.924644] ACPI _OSC control for PCIe not granted, disabling ASPM
Feb 14 18:12:27 debian kernel: [    0.933465] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 18:12:27 debian kernel: [    0.933577] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 18:12:27 debian kernel: [    0.933707] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 18:12:27 debian kernel: [    0.933833] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 18:12:27 debian kernel: [    0.933938] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 18:12:27 debian kernel: [    0.934020] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 18:12:27 debian kernel: [    0.934100] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 18:12:27 debian kernel: [    0.934179] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 18:12:27 debian kernel: [    0.934382] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
Feb 14 18:12:27 debian kernel: [    0.934382] vgaarb: loaded
Feb 14 18:12:27 debian kernel: [    0.934382] vgaarb: bridge control possible 0000:00:01.0
Feb 14 18:12:27 debian kernel: [    0.934382] PCI: Using ACPI for IRQ routing
Feb 14 18:12:27 debian kernel: [    0.936144] PCI: pci_cache_line_size set to 64 bytes
Feb 14 18:12:27 debian kernel: [    0.936274] reserve RAM buffer: 000000000006e000 - 000000000006ffff 
Feb 14 18:12:27 debian kernel: [    0.936278] reserve RAM buffer: 0000000000086000 - 000000000008ffff 
Feb 14 18:12:27 debian kernel: [    0.936282] reserve RAM buffer: 0000000097c34000 - 0000000097ffffff 
Feb 14 18:12:27 debian kernel: [    0.936285] reserve RAM buffer: 000000009f28f000 - 000000009fffffff 
Feb 14 18:12:27 debian kernel: [    0.936289] reserve RAM buffer: 000000009fc00000 - 000000009fffffff 
Feb 14 18:12:27 debian kernel: [    0.936292] reserve RAM buffer: 000000021f000000 - 000000021fffffff 
Feb 14 18:12:27 debian kernel: [    0.936489] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb 14 18:12:27 debian kernel: [    0.936496] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Feb 14 18:12:27 debian kernel: [    0.938521] Switching to clocksource hpet
Feb 14 18:12:27 debian kernel: [    0.938648] pnp: PnP ACPI init
Feb 14 18:12:27 debian kernel: [    0.938673] ACPI: bus type pnp registered
Feb 14 18:12:27 debian kernel: [    0.938873] pnp 00:00: [bus 00-ff]
Feb 14 18:12:27 debian kernel: [    0.938878] pnp 00:00: [io  0x0000-0x0cf7 window]
Feb 14 18:12:27 debian kernel: [    0.938881] pnp 00:00: [io  0x0d00-0xffff window]
Feb 14 18:12:27 debian kernel: [    0.938884] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Feb 14 18:12:27 debian kernel: [    0.938887] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Feb 14 18:12:27 debian kernel: [    0.938891] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Feb 14 18:12:27 debian kernel: [    0.938893] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Feb 14 18:12:27 debian kernel: [    0.938896] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Feb 14 18:12:27 debian kernel: [    0.938899] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Feb 14 18:12:27 debian kernel: [    0.938902] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Feb 14 18:12:27 debian kernel: [    0.938905] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Feb 14 18:12:27 debian kernel: [    0.938908] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Feb 14 18:12:27 debian kernel: [    0.938911] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Feb 14 18:12:27 debian kernel: [    0.938914] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Feb 14 18:12:27 debian kernel: [    0.938916] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Feb 14 18:12:27 debian kernel: [    0.938919] pnp 00:00: [mem 0x000ec000-0x000effff window]
Feb 14 18:12:27 debian kernel: [    0.938922] pnp 00:00: [mem 0xe0000000-0xf7ffffff window]
Feb 14 18:12:27 debian kernel: [    0.938925] pnp 00:00: [mem 0xfc000000-0xfed3ffff window]
Feb 14 18:12:27 debian kernel: [    0.938928] pnp 00:00: [mem 0xfed45000-0xffffffff window]
Feb 14 18:12:27 debian kernel: [    0.938931] pnp 00:00: [io  0x0cf8-0x0cff]
Feb 14 18:12:27 debian kernel: [    0.939018] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Feb 14 18:12:27 debian kernel: [    0.939116] pnp 00:01: [mem 0xfec00000-0xfec01fff]
Feb 14 18:12:27 debian kernel: [    0.939120] pnp 00:01: [mem 0xfee00000-0xfee00fff]
Feb 14 18:12:27 debian kernel: [    0.939193] system 00:01: [mem 0xfec00000-0xfec01fff] could not be reserved
Feb 14 18:12:27 debian kernel: [    0.939197] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
Feb 14 18:12:27 debian kernel: [    0.939202] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 14 18:12:27 debian kernel: [    0.939335] pnp 00:02: [irq 0 disabled]
Feb 14 18:12:27 debian kernel: [    0.939350] pnp 00:02: [irq 8]
Feb 14 18:12:27 debian kernel: [    0.939353] pnp 00:02: [mem 0xfed00000-0xfed003ff]
Feb 14 18:12:27 debian kernel: [    0.939395] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
Feb 14 18:12:27 debian kernel: [    0.939477] pnp 00:03: [io  0x0000-0x000f]
Feb 14 18:12:27 debian kernel: [    0.939480] pnp 00:03: [io  0x0081-0x008f]
Feb 14 18:12:27 debian kernel: [    0.939483] pnp 00:03: [io  0x00c0-0x00df]
Feb 14 18:12:27 debian kernel: [    0.939485] pnp 00:03: [dma 4]
Feb 14 18:12:27 debian kernel: [    0.939539] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Feb 14 18:12:27 debian kernel: [    0.939556] pnp 00:04: [io  0x00f0-0x00fe]
Feb 14 18:12:27 debian kernel: [    0.939563] pnp 00:04: [irq 13]
Feb 14 18:12:27 debian kernel: [    0.939608] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Feb 14 18:12:27 debian kernel: [    0.939652] pnp 00:05: [io  0x0070-0x0071]
Feb 14 18:12:27 debian kernel: [    0.939700] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb 14 18:12:27 debian kernel: [    0.939714] pnp 00:06: [io  0x0061]
Feb 14 18:12:27 debian kernel: [    0.939761] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Feb 14 18:12:27 debian kernel: [    0.939779] pnp 00:07: [io  0x0060]
Feb 14 18:12:27 debian kernel: [    0.939782] pnp 00:07: [io  0x0064]
Feb 14 18:12:27 debian kernel: [    0.939789] pnp 00:07: [irq 1]
Feb 14 18:12:27 debian kernel: [    0.939835] pnp 00:07: Plug and Play ACPI device, IDs TOS1101 PNP0303 (active)
Feb 14 18:12:27 debian kernel: [    0.939855] pnp 00:08: [irq 12]
Feb 14 18:12:27 debian kernel: [    0.939904] pnp 00:08: Plug and Play ACPI device, IDs TOS0330 SYN1900 SYN0002 PNP0f13 (active)
Feb 14 18:12:27 debian kernel: [    0.939919] pnp 00:09: [io  0x0b20-0x0b3f]
Feb 14 18:12:27 debian kernel: [    0.939923] pnp 00:09: IRQ 7 override to edge, high
Feb 14 18:12:27 debian kernel: [    0.939929] pnp 00:09: [irq 7]
Feb 14 18:12:27 debian kernel: [    0.939978] pnp 00:09: Plug and Play ACPI device, IDs SMB0001 (active)
Feb 14 18:12:27 debian kernel: [    0.940015] pnp 00:0a: [io  0x0010-0x001f]
Feb 14 18:12:27 debian kernel: [    0.940018] pnp 00:0a: [io  0x002e-0x002f]
Feb 14 18:12:27 debian kernel: [    0.940021] pnp 00:0a: [io  0x0062]
Feb 14 18:12:27 debian kernel: [    0.940023] pnp 00:0a: [io  0x0066]
Feb 14 18:12:27 debian kernel: [    0.940026] pnp 00:0a: [io  0x0068]
Feb 14 18:12:27 debian kernel: [    0.940028] pnp 00:0a: [io  0x006c]
Feb 14 18:12:27 debian kernel: [    0.940030] pnp 00:0a: [io  0x0072-0x0073]
Feb 14 18:12:27 debian kernel: [    0.940033] pnp 00:0a: [io  0x0080]
Feb 14 18:12:27 debian kernel: [    0.940035] pnp 00:0a: [io  0x00b0-0x00b1]
Feb 14 18:12:27 debian kernel: [    0.940038] pnp 00:0a: [io  0x0092]
Feb 14 18:12:27 debian kernel: [    0.940040] pnp 00:0a: [io  0x0400-0x04cf]
Feb 14 18:12:27 debian kernel: [    0.940043] pnp 00:0a: [io  0x04d0-0x04d1]
Feb 14 18:12:27 debian kernel: [    0.940045] pnp 00:0a: [io  0x04d6]
Feb 14 18:12:27 debian kernel: [    0.940048] pnp 00:0a: [io  0x0680-0x06ff]
Feb 14 18:12:27 debian kernel: [    0.940050] pnp 00:0a: [io  0x077a]
Feb 14 18:12:27 debian kernel: [    0.940052] pnp 00:0a: [io  0x0c00-0x0c01]
Feb 14 18:12:27 debian kernel: [    0.940057] pnp 00:0a: [io  0x0c14]
Feb 14 18:12:27 debian kernel: [    0.940059] pnp 00:0a: [io  0x0c50-0x0c52]
Feb 14 18:12:27 debian kernel: [    0.940062] pnp 00:0a: [io  0x0c6c]
Feb 14 18:12:27 debian kernel: [    0.940064] pnp 00:0a: [io  0x0c6f]
Feb 14 18:12:27 debian kernel: [    0.940066] pnp 00:0a: [io  0x0cd0-0x0cdb]
Feb 14 18:12:27 debian kernel: [    0.940069] pnp 00:0a: [io  0x0840-0x0847]
Feb 14 18:12:27 debian kernel: [    0.940155] system 00:0a: [io  0x0400-0x04cf] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940159] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940163] system 00:0a: [io  0x04d6] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940166] system 00:0a: [io  0x0680-0x06ff] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940170] system 00:0a: [io  0x077a] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940173] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940178] system 00:0a: [io  0x0c14] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940182] system 00:0a: [io  0x0c50-0x0c52] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940186] system 00:0a: [io  0x0c6c] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940189] system 00:0a: [io  0x0c6f] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940192] system 00:0a: [io  0x0cd0-0x0cdb] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940196] system 00:0a: [io  0x0840-0x0847] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940200] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 14 18:12:27 debian kernel: [    0.940283] pnp 00:0b: [mem 0xff700000-0xff70ffff]
Feb 14 18:12:27 debian kernel: [    0.940286] pnp 00:0b: [mem 0x000e0000-0x000fffff]
Feb 14 18:12:27 debian kernel: [    0.940289] pnp 00:0b: [mem 0xff800000-0xffffffff]
Feb 14 18:12:27 debian kernel: [    0.940364] system 00:0b: [mem 0xff700000-0xff70ffff] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940368] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
Feb 14 18:12:27 debian kernel: [    0.940372] system 00:0b: [mem 0xff800000-0xffffffff] has been reserved
Feb 14 18:12:27 debian kernel: [    0.940376] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb 14 18:12:27 debian kernel: [    0.942125] pnp: PnP ACPI: found 12 devices
Feb 14 18:12:27 debian kernel: [    0.942128] ACPI: ACPI bus type pnp unregistered
Feb 14 18:12:27 debian kernel: [    0.950408] pci 0000:00:01.0: address space collision: [mem 0xfffe0000-0xffffffff pref] conflicts with reserved [mem 0xff800000-0xffffffff]
Feb 14 18:12:27 debian kernel: [    0.950428] PCI: max bus depth: 1 pci_try_num: 2
Feb 14 18:12:27 debian kernel: [    0.950460] pci 0000:00:01.0: BAR 6: assigned [mem 0xf2c80000-0xf2c9ffff pref]
Feb 14 18:12:27 debian kernel: [    0.950470] pci 0000:00:02.4: BAR 15: assigned [mem 0xf2d00000-0xf2efffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.950475] pci 0000:00:02.4: BAR 13: assigned [io  0x1000-0x1fff]
Feb 14 18:12:27 debian kernel: [    0.950479] pci 0000:00:02.2: PCI bridge to [bus 01-04]
Feb 14 18:12:27 debian kernel: [    0.950482] pci 0000:00:02.2:   bridge window [io  0x2000-0x2fff]
Feb 14 18:12:27 debian kernel: [    0.950487] pci 0000:00:02.2:   bridge window [mem 0xf1000000-0xf1ffffff]
Feb 14 18:12:27 debian kernel: [    0.950491] pci 0000:00:02.2:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.950497] pci 0000:00:02.3: PCI bridge to [bus 05-05]
Feb 14 18:12:27 debian kernel: [    0.950501] pci 0000:00:02.3:   bridge window [mem 0xf2b00000-0xf2bfffff]
Feb 14 18:12:27 debian kernel: [    0.950508] pci 0000:00:02.4: PCI bridge to [bus 06-06]
Feb 14 18:12:27 debian kernel: [    0.950511] pci 0000:00:02.4:   bridge window [io  0x1000-0x1fff]
Feb 14 18:12:27 debian kernel: [    0.950516] pci 0000:00:02.4:   bridge window [mem 0xf2a00000-0xf2afffff]
Feb 14 18:12:27 debian kernel: [    0.950520] pci 0000:00:02.4:   bridge window [mem 0xf2d00000-0xf2efffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.950545] pci 0000:00:02.2: setting latency timer to 64
Feb 14 18:12:27 debian kernel: [    0.950563] pci 0000:00:02.3: setting latency timer to 64
Feb 14 18:12:27 debian kernel: [    0.950577] pci 0000:00:02.4: setting latency timer to 64
Feb 14 18:12:27 debian kernel: [    0.950581] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Feb 14 18:12:27 debian kernel: [    0.950584] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Feb 14 18:12:27 debian kernel: [    0.950586] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Feb 14 18:12:27 debian kernel: [    0.950589] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Feb 14 18:12:27 debian kernel: [    0.950592] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Feb 14 18:12:27 debian kernel: [    0.950595] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Feb 14 18:12:27 debian kernel: [    0.950597] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
Feb 14 18:12:27 debian kernel: [    0.950600] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
Feb 14 18:12:27 debian kernel: [    0.950603] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
Feb 14 18:12:27 debian kernel: [    0.950605] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
Feb 14 18:12:27 debian kernel: [    0.950608] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
Feb 14 18:12:27 debian kernel: [    0.950610] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
Feb 14 18:12:27 debian kernel: [    0.950613] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
Feb 14 18:12:27 debian kernel: [    0.950616] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
Feb 14 18:12:27 debian kernel: [    0.950618] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
Feb 14 18:12:27 debian kernel: [    0.950621] pci_bus 0000:00: resource 19 [mem 0xe0000000-0xf7ffffff]
Feb 14 18:12:27 debian kernel: [    0.950624] pci_bus 0000:00: resource 20 [mem 0xfc000000-0xfed3ffff]
Feb 14 18:12:27 debian kernel: [    0.950626] pci_bus 0000:00: resource 21 [mem 0xfed45000-0xffffffff]
Feb 14 18:12:27 debian kernel: [    0.950629] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
Feb 14 18:12:27 debian kernel: [    0.950632] pci_bus 0000:01: resource 1 [mem 0xf1000000-0xf1ffffff]
Feb 14 18:12:27 debian kernel: [    0.950635] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf0ffffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.950638] pci_bus 0000:05: resource 1 [mem 0xf2b00000-0xf2bfffff]
Feb 14 18:12:27 debian kernel: [    0.950640] pci_bus 0000:06: resource 0 [io  0x1000-0x1fff]
Feb 14 18:12:27 debian kernel: [    0.950643] pci_bus 0000:06: resource 1 [mem 0xf2a00000-0xf2afffff]
Feb 14 18:12:27 debian kernel: [    0.950646] pci_bus 0000:06: resource 2 [mem 0xf2d00000-0xf2efffff 64bit pref]
Feb 14 18:12:27 debian kernel: [    0.950786] NET: Registered protocol family 2
Feb 14 18:12:27 debian kernel: [    0.955974] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Feb 14 18:12:27 debian kernel: [    0.957579] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Feb 14 18:12:27 debian kernel: [    0.960198] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 14 18:12:27 debian kernel: [    0.960513] TCP: Hash tables configured (established 524288 bind 65536)
Feb 14 18:12:27 debian kernel: [    0.960517] TCP reno registered 
Feb 14 18:12:27 debian kernel: [    0.960541] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Feb 14 18:12:27 debian kernel: [    0.960599] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Feb 14 18:12:27 debian kernel: [    0.960841] NET: Registered protocol family 1
Feb 14 18:12:27 debian kernel: [    0.960864] pci 0000:00:01.0: Boot video device
Feb 14 18:12:27 debian kernel: [    0.960896] ACPI: Cannot set device to a higher-powered state than parent
Feb 14 18:12:27 debian kernel: [    0.960900] ACPI: Cannot set device to a higher-powered state than parent
Feb 14 18:12:27 debian kernel: [    0.969888] PCI: CLS 64 bytes, default 64
Feb 14 18:12:27 debian kernel: [    0.969966] Unpacking initramfs...
Feb 14 18:12:27 debian kernel: [    1.255245] Freeing initrd memory: 11020k freed
Feb 14 18:12:27 debian kernel: [    1.258877] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Feb 14 18:12:27 debian kernel: [    1.258885] Placing 64MB software IO TLB between ffff880091540000 - ffff880095540000
Feb 14 18:12:27 debian kernel: [    1.258888] software IO TLB at phys 0x91540000 - 0x95540000
Feb 14 18:12:27 debian kernel: [    1.258930] Simple Boot Flag at 0x44 set to 0x1
Feb 14 18:12:27 debian kernel: [    1.259439] perf: AMD IBS detected (0x000000ff)
Feb 14 18:12:27 debian kernel: [    1.259756] audit: initializing netlink socket (disabled)
Feb 14 18:12:27 debian kernel: [    1.259772] type=2000 audit(1423933931.252:1): initialized
Feb 14 18:12:27 debian kernel: [    1.276579] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb 14 18:12:27 debian kernel: [    1.278024] VFS: Disk quotas dquot_6.5.2
Feb 14 18:12:27 debian kernel: [    1.278069] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 14 18:12:27 debian kernel: [    1.278164] msgmni has been set to 13911
Feb 14 18:12:27 debian kernel: [    1.278398] alg: No test for stdrng (krng)
Feb 14 18:12:27 debian kernel: [    1.278442] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Feb 14 18:12:27 debian kernel: [    1.278447] io scheduler noop registered
Feb 14 18:12:27 debian kernel: [    1.278449] io scheduler deadline registered
Feb 14 18:12:27 debian kernel: [    1.278483] io scheduler cfq registered (default)
Feb 14 18:12:27 debian kernel: [    1.278749] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 14 18:12:27 debian kernel: [    1.278777] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 14 18:12:27 debian kernel: [    1.278780] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Feb 14 18:12:27 debian kernel: [    1.279239] efifb: probing for efifb
Feb 14 18:12:27 debian kernel: [    1.279986] efifb: framebuffer at 0xe0000000, mapped to 0xffffc9000a280000, using 5632k, total 5632k
Feb 14 18:12:27 debian kernel: [    1.279989] efifb: mode is 1600x900x32, linelength=6400, pages=1
Feb 14 18:12:27 debian kernel: [    1.279991] efifb: scrolling: redraw
Feb 14 18:12:27 debian kernel: [    1.279995] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Feb 14 18:12:27 debian kernel: [    1.286711] Console: switching to colour frame buffer device 200x56
Feb 14 18:12:27 debian kernel: [    1.292755] fb0: EFI VGA frame buffer device
Feb 14 18:12:27 debian kernel: [    1.292799] ERST: Table is not found!
Feb 14 18:12:27 debian kernel: [    1.292801] GHES: HEST is not enabled!
Feb 14 18:12:27 debian kernel: [    1.292890] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb 14 18:12:27 debian kernel: [    1.484904] Linux agpgart interface v0.103
Feb 14 18:12:27 debian kernel: [    1.485084] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb 14 18:12:27 debian kernel: [    1.487652] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 14 18:12:27 debian kernel: [    1.487663] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 14 18:12:27 debian kernel: [    1.487875] mousedev: PS/2 mouse device common for all mice
Feb 14 18:12:27 debian kernel: [    1.487920] rtc_cmos 00:05: RTC can wake from S4
Feb 14 18:12:27 debian kernel: [    1.488049] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Feb 14 18:12:27 debian kernel: [    1.488072] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Feb 14 18:12:27 debian kernel: [    1.488089] cpuidle: using governor ladder
Feb 14 18:12:27 debian kernel: [    1.488091] cpuidle: using governor menu
Feb 14 18:12:27 debian kernel: [    1.488371] TCP cubic registered
Feb 14 18:12:27 debian kernel: [    1.488476] NET: Registered protocol family 10
Feb 14 18:12:27 debian kernel: [    1.489094] Mobile IPv6
Feb 14 18:12:27 debian kernel: [    1.489099] NET: Registered protocol family 17
Feb 14 18:12:27 debian kernel: [    1.489104] Registering the dns_resolver key type
Feb 14 18:12:27 debian kernel: [    1.489353] PM: Hibernation image not present or could not be loaded.
Feb 14 18:12:27 debian kernel: [    1.489372] registered taskstats version 1
Feb 14 18:12:27 debian kernel: [    1.490459] rtc_cmos 00:05: setting system clock to 2015-02-14 17:12:12 UTC (1423933932)
Feb 14 18:12:27 debian kernel: [    1.490566] Initializing network drop monitor service
Feb 14 18:12:27 debian kernel: [    1.492223] Freeing unused kernel memory: 576k freed
Feb 14 18:12:27 debian kernel: [    1.492378] Write protecting the kernel read-only data: 6144k
Feb 14 18:12:27 debian kernel: [    1.495647] Freeing unused kernel memory: 644k freed
Feb 14 18:12:27 debian kernel: [    1.499205] Freeing unused kernel memory: 688k freed
Feb 14 18:12:27 debian kernel: [    1.502413] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
Feb 14 18:12:27 debian kernel: [    1.537117] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb 14 18:12:27 debian kernel: [    1.537204] r8169 0000:01:00.0: (unregistered net_device): unknown MAC, using family default
Feb 14 18:12:27 debian kernel: [    1.537213] r8169 0000:01:00.0: setting latency timer to 64
Feb 14 18:12:27 debian kernel: [    1.537267] r8169 0000:01:00.0: irq 72 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    1.537935] r8169 0000:01:00.0: eth0: RTL8101e at 0xffffc90000046000, 00:8c:fa:86:90:5a, XID 04900000 IRQ 72
Feb 14 18:12:27 debian kernel: [    1.545919] usbcore: registered new interface driver usbfs
Feb 14 18:12:27 debian kernel: [    1.545953] usbcore: registered new interface driver hub
Feb 14 18:12:27 debian kernel: [    1.559361] usbcore: registered new device driver usb
Feb 14 18:12:27 debian kernel: [    1.560194] SCSI subsystem initialized
Feb 14 18:12:27 debian kernel: [    1.560263] ACPI: Cannot set device to a higher-powered state than parent
Feb 14 18:12:27 debian kernel: [    1.560269] ACPI: Cannot set device to a higher-powered state than parent
Feb 14 18:12:27 debian kernel: [    1.560321] xhci_hcd 0000:00:10.0: setting latency timer to 64
Feb 14 18:12:27 debian kernel: [    1.560326] xhci_hcd 0000:00:10.0: xHCI Host Controller
Feb 14 18:12:27 debian kernel: [    1.560364] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb 14 18:12:27 debian kernel: [    1.560646] xhci_hcd 0000:00:10.0: irq 73 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    1.560654] xhci_hcd 0000:00:10.0: irq 74 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    1.560661] xhci_hcd 0000:00:10.0: irq 75 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    1.560668] xhci_hcd 0000:00:10.0: irq 76 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    1.560675] xhci_hcd 0000:00:10.0: irq 77 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    1.560807] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Feb 14 18:12:27 debian kernel: [    1.560810] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 18:12:27 debian kernel: [    1.560813] usb usb1: Product: xHCI Host Controller
Feb 14 18:12:27 debian kernel: [    1.560816] usb usb1: Manufacturer: Linux 3.2.0-4-amd64 xhci_hcd
Feb 14 18:12:27 debian kernel: [    1.560818] usb usb1: SerialNumber: 0000:00:10.0
Feb 14 18:12:27 debian kernel: [    1.564669] xHCI xhci_add_endpoint called for root hub
Feb 14 18:12:27 debian kernel: [    1.564673] xHCI xhci_check_bandwidth called for root hub
Feb 14 18:12:27 debian kernel: [    1.564738] hub 1-0:1.0: USB hub found
Feb 14 18:12:27 debian kernel: [    1.564742] libata version 3.00 loaded.
Feb 14 18:12:27 debian kernel: [    1.564749] hub 1-0:1.0: 2 ports detected
Feb 14 18:12:27 debian kernel: [    1.564871] xhci_hcd 0000:00:10.0: xHCI Host Controller
Feb 14 18:12:27 debian kernel: [    1.564883] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Feb 14 18:12:27 debian kernel: [    1.564923] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Feb 14 18:12:27 debian kernel: [    1.564927] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 18:12:27 debian kernel: [    1.564930] usb usb2: Product: xHCI Host Controller
Feb 14 18:12:27 debian kernel: [    1.564933] usb usb2: Manufacturer: Linux 3.2.0-4-amd64 xhci_hcd
Feb 14 18:12:27 debian kernel: [    1.564935] usb usb2: SerialNumber: 0000:00:10.0
Feb 14 18:12:27 debian kernel: [    1.565045] xHCI xhci_add_endpoint called for root hub
Feb 14 18:12:27 debian kernel: [    1.565048] xHCI xhci_check_bandwidth called for root hub
Feb 14 18:12:27 debian kernel: [    1.565091] hub 2-0:1.0: USB hub found
Feb 14 18:12:27 debian kernel: [    1.565099] hub 2-0:1.0: 2 ports detected
Feb 14 18:12:27 debian kernel: [    1.565348] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 14 18:12:27 debian kernel: [    1.582173] ACPI: Fan [FAN1] (off)
Feb 14 18:12:27 debian kernel: [    1.582727] thermal LNXTHERM:00: registered as thermal_zone0
Feb 14 18:12:27 debian kernel: [    1.582731] ACPI: Thermal Zone [THZN] (26 C)
Feb 14 18:12:27 debian kernel: [    1.592194] ehci_hcd 0000:00:12.0: EHCI Host Controller
Feb 14 18:12:27 debian kernel: [    1.592217] ehci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Feb 14 18:12:27 debian kernel: [    1.592230] ehci_hcd 0000:00:12.0: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Feb 14 18:12:27 debian kernel: [    1.592257] ehci_hcd 0000:00:12.0: debug port 2
Feb 14 18:12:27 debian kernel: [    1.592294] ehci_hcd 0000:00:12.0: irq 18, io mem 0xf2c6d000
Feb 14 18:12:27 debian kernel: [    1.604191] ehci_hcd 0000:00:12.0: USB 2.0 started, EHCI 1.00
Feb 14 18:12:27 debian kernel: [    1.604240] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Feb 14 18:12:27 debian kernel: [    1.604243] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 18:12:27 debian kernel: [    1.604247] usb usb3: Product: EHCI Host Controller
Feb 14 18:12:27 debian kernel: [    1.604249] usb usb3: Manufacturer: Linux 3.2.0-4-amd64 ehci_hcd
Feb 14 18:12:27 debian kernel: [    1.604252] usb usb3: SerialNumber: 0000:00:12.0
Feb 14 18:12:27 debian kernel: [    1.604459] hub 3-0:1.0: USB hub found
Feb 14 18:12:27 debian kernel: [    1.604465] hub 3-0:1.0: 2 ports detected
Feb 14 18:12:27 debian kernel: [    1.604641] ehci_hcd 0000:00:13.0: EHCI Host Controller
Feb 14 18:12:27 debian kernel: [    1.604659] ehci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
Feb 14 18:12:27 debian kernel: [    1.604668] ehci_hcd 0000:00:13.0: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Feb 14 18:12:27 debian kernel: [    1.604690] ehci_hcd 0000:00:13.0: debug port 2
Feb 14 18:12:27 debian kernel: [    1.604709] ehci_hcd 0000:00:13.0: irq 18, io mem 0xf2c6c000
Feb 14 18:12:27 debian kernel: [    1.616289] ehci_hcd 0000:00:13.0: USB 2.0 started, EHCI 1.00
Feb 14 18:12:27 debian kernel: [    1.616333] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
Feb 14 18:12:27 debian kernel: [    1.616336] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 18:12:27 debian kernel: [    1.616339] usb usb4: Product: EHCI Host Controller
Feb 14 18:12:27 debian kernel: [    1.616342] usb usb4: Manufacturer: Linux 3.2.0-4-amd64 ehci_hcd
Feb 14 18:12:27 debian kernel: [    1.616344] usb usb4: SerialNumber: 0000:00:13.0
Feb 14 18:12:27 debian kernel: [    1.616557] hub 4-0:1.0: USB hub found
Feb 14 18:12:27 debian kernel: [    1.616564] hub 4-0:1.0: 2 ports detected
Feb 14 18:12:27 debian kernel: [    1.616690] ahci 0000:00:11.0: version 3.0
Feb 14 18:12:27 debian kernel: [    1.616794] ahci 0000:00:11.0: irq 78 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    1.616858] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
Feb 14 18:12:27 debian kernel: [    1.616863] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp fbs pio slum part 
Feb 14 18:12:27 debian kernel: [    1.617301] scsi0 : ahci
Feb 14 18:12:27 debian kernel: [    1.617461] scsi1 : ahci
Feb 14 18:12:27 debian kernel: [    1.711993] ata1: SATA max UDMA/133 abar m1024@0xf2c6e000 port 0xf2c6e100 irq 78
Feb 14 18:12:27 debian kernel: [    1.711999] ata2: SATA max UDMA/133 abar m1024@0xf2c6e000 port 0xf2c6e180 irq 78
Feb 14 18:12:27 debian kernel: [    1.916209] usb 3-1: new high-speed USB device number 2 using ehci_hcd
Feb 14 18:12:27 debian kernel: [    2.049284] usb 3-1: New USB device found, idVendor=0438, idProduct=7900
Feb 14 18:12:27 debian kernel: [    2.049289] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Feb 14 18:12:27 debian kernel: [    2.049681] hub 3-1:1.0: USB hub found
Feb 14 18:12:27 debian kernel: [    2.049760] hub 3-1:1.0: 4 ports detected
Feb 14 18:12:27 debian kernel: [    2.160218] usb 4-1: new high-speed USB device number 2 using ehci_hcd
Feb 14 18:12:27 debian kernel: [    2.204212] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 14 18:12:27 debian kernel: [    2.204237] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 14 18:12:27 debian kernel: [    2.207477] ata2.00: ATAPI: TSSTcorp CDDVDW SU-208FB, TF01, max UDMA/100
Feb 14 18:12:27 debian kernel: [    2.212392] ata2.00: configured for UDMA/100
Feb 14 18:12:27 debian kernel: [    2.255349] ata1.00: ATA-8: TOSHIBA MQ01ABD100, AX1P4M, max UDMA/100
Feb 14 18:12:27 debian kernel: [    2.255354] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Feb 14 18:12:27 debian kernel: [    2.256176] Refined TSC clocksource calibration: 1996.255 MHz.
Feb 14 18:12:27 debian kernel: [    2.256188] Switching to clocksource tsc
Feb 14 18:12:27 debian kernel: [    2.257298] ata1.00: configured for UDMA/100
Feb 14 18:12:27 debian kernel: [    2.257548] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD1 AX1P PQ: 0 ANSI: 5
Feb 14 18:12:27 debian kernel: [    2.262044] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SU-208FB  TF01 PQ: 0 ANSI: 5
Feb 14 18:12:27 debian kernel: [    2.266182] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Feb 14 18:12:27 debian kernel: [    2.266258] sd 0:0:0:0: [sda] Write Protect is off
Feb 14 18:12:27 debian kernel: [    2.266262] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 14 18:12:27 debian kernel: [    2.266293] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 18:12:27 debian kernel: [    2.278590] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Feb 14 18:12:27 debian kernel: [    2.278596] cdrom: Uniform CD-ROM driver Revision: 3.20
Feb 14 18:12:27 debian kernel: [    2.278855] sr 1:0:0:0: Attached scsi CD-ROM sr0
Feb 14 18:12:27 debian kernel: [    2.293488] usb 4-1: New USB device found, idVendor=0438, idProduct=7900
Feb 14 18:12:27 debian kernel: [    2.293493] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Feb 14 18:12:27 debian kernel: [    2.293809] hub 4-1:1.0: USB hub found
Feb 14 18:12:27 debian kernel: [    2.293888] hub 4-1:1.0: 4 ports detected
Feb 14 18:12:27 debian kernel: [    2.385294]  sda: sda1 sda2 sda3 sda4
Feb 14 18:12:27 debian kernel: [    2.385888] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 14 18:12:27 debian kernel: [    2.389012] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb 14 18:12:27 debian kernel: [    2.389091] sr 1:0:0:0: Attached scsi generic sg1 type 5
Feb 14 18:12:27 debian kernel: [    2.581106] usb 4-1.1: new full-speed USB device number 3 using ehci_hcd
Feb 14 18:12:27 debian kernel: [    2.690965] usb 4-1.1: New USB device found, idVendor=0930, idProduct=0225
Feb 14 18:12:27 debian kernel: [    2.690971] usb 4-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 14 18:12:27 debian kernel: [    2.690974] usb 4-1.1: Product: BCM43142A0
Feb 14 18:12:27 debian kernel: [    2.690976] usb 4-1.1: Manufacturer: Broadcom Corp
Feb 14 18:12:27 debian kernel: [    2.690979] usb 4-1.1: SerialNumber: 645A04D4D14B
Feb 14 18:12:27 debian kernel: [    2.776602] usb 4-1.2: new high-speed USB device number 4 using ehci_hcd
Feb 14 18:12:27 debian kernel: [    2.967272] usb 4-1.2: New USB device found, idVendor=10f1, idProduct=1a5b
Feb 14 18:12:27 debian kernel: [    2.967277] usb 4-1.2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Feb 14 18:12:27 debian kernel: [    2.967281] usb 4-1.2: Product: TOSHIBA Web Camera - HD
Feb 14 18:12:27 debian kernel: [    2.967283] usb 4-1.2: Manufacturer: Sonix Technology Co., Ltd.
Feb 14 18:12:27 debian kernel: [    3.192506] PM: Starting manual resume from disk
Feb 14 18:12:27 debian kernel: [    3.192511] PM: Hibernation image partition 8:3 present
Feb 14 18:12:27 debian kernel: [    3.192513] PM: Looking for hibernation image.
Feb 14 18:12:27 debian kernel: [    3.225062] PM: Image not found (code -22)
Feb 14 18:12:27 debian kernel: [    3.225066] PM: Hibernation image not present or could not be loaded.
Feb 14 18:12:27 debian kernel: [    3.592106] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Feb 14 18:12:27 debian kernel: [    6.066906] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Feb 14 18:12:27 debian kernel: [    6.066917] ACPI: Power Button [PWRB]
Feb 14 18:12:27 debian kernel: [    6.067008] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
Feb 14 18:12:27 debian kernel: [    6.067371] ACPI: Lid Switch [LID0]
Feb 14 18:12:27 debian kernel: [    6.067446] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Feb 14 18:12:27 debian kernel: [    6.067451] ACPI: Power Button [PWRF]
Feb 14 18:12:27 debian kernel: [    6.140682] acpi device:00: registered as cooling_device1
Feb 14 18:12:27 debian kernel: [    6.140766] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
Feb 14 18:12:27 debian kernel: [    6.140774] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Feb 14 18:12:27 debian kernel: [    6.227990] wmi: Mapper loaded
Feb 14 18:12:27 debian kernel: [    6.235101] ACPI: acpi_idle registered with cpuidle
Feb 14 18:12:27 debian kernel: [    6.278397] input: PC Speaker as /devices/platform/pcspkr/input/input5
Feb 14 18:12:27 debian kernel: [    6.382286] EFI Variables Facility v0.08 2004-May-17
Feb 14 18:12:27 debian kernel: [    6.469547] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
Feb 14 18:12:27 debian kernel: [    6.494749] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMB0 [io 0xb00-0xb0f]
Feb 14 18:12:27 debian kernel: [    6.494757] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb 14 18:12:27 debian kernel: [    6.508942] alg: No test for __gcm-aes-aesni (__driver-gcm-aes-aesni)
Feb 14 18:12:27 debian kernel: [    6.520130] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
Feb 14 18:12:27 debian kernel: [    6.770676] powernow-k8: Found 1 AMD A8-6410 APU with AMD Radeon R5 Graphics     (4 cpu cores) (version 2.20.00)
Feb 14 18:12:27 debian kernel: [    6.770693] powernow-k8: Core Performance Boosting: on.
Feb 14 18:12:27 debian kernel: [    6.770792] powernow-k8:    0 : pstate 0 (2000 MHz)
Feb 14 18:12:27 debian kernel: [    6.770795] powernow-k8:    1 : pstate 1 (1800 MHz)
Feb 14 18:12:27 debian kernel: [    6.770797] powernow-k8:    2 : pstate 2 (1600 MHz)
Feb 14 18:12:27 debian kernel: [    6.770799] powernow-k8:    3 : pstate 3 (1400 MHz)
Feb 14 18:12:27 debian kernel: [    6.770801] powernow-k8:    4 : pstate 4 (1200 MHz)
Feb 14 18:12:27 debian kernel: [    6.770804] powernow-k8:    5 : pstate 5 (1000 MHz)
Feb 14 18:12:27 debian kernel: [    6.814335] ACPI: Battery Slot [BAT0] (battery present)
Feb 14 18:12:27 debian kernel: [    6.814593] ACPI: AC Adapter [ADP0] (on-line)
Feb 14 18:12:27 debian kernel: [    6.957044] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
Feb 14 18:12:27 debian kernel: [    6.957833] input: Toshiba input device as /devices/virtual/input/input6
Feb 14 18:12:27 debian kernel: [    7.061101] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
Feb 14 18:12:27 debian kernel: [    7.076224] Registered led device: toshiba::illumination
Feb 14 18:12:27 debian kernel: [    7.094181] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Feb 14 18:12:27 debian kernel: [    7.115807] cfg80211: Calling CRDA to update world regulatory domain
Feb 14 18:12:27 debian kernel: [    7.356676] wl: module license 'unspecified' taints kernel.
Feb 14 18:12:27 debian kernel: [    7.356686] Disabling lock debugging due to kernel taint
Feb 14 18:12:27 debian kernel: [    7.397021] wl 0000:05:00.0: setting latency timer to 64
Feb 14 18:12:27 debian kernel: [    7.430269] eth1: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
Feb 14 18:12:27 debian kernel: [    7.430432] snd_hda_intel 0000:00:01.1: irq 79 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    7.430458] snd_hda_intel 0000:00:01.1: setting latency timer to 64
Feb 14 18:12:27 debian kernel: [    8.198113] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
Feb 14 18:12:27 debian kernel: [    8.198374] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input8
Feb 14 18:12:27 debian kernel: [    8.199194] snd_hda_intel 0000:00:14.2: irq 80 for MSI/MSI-X
Feb 14 18:12:27 debian kernel: [    8.357649] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
Feb 14 18:12:27 debian kernel: [    8.361243] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
Feb 14 18:12:27 debian kernel: [    8.361358] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
Feb 14 18:12:27 debian kernel: [    8.502922] cfg80211: World regulatory domain updated:
Feb 14 18:12:27 debian kernel: [    8.502933] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 14 18:12:27 debian kernel: [    8.502941] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 18:12:27 debian kernel: [    8.502948] cfg80211:     (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 18:12:27 debian kernel: [    8.502954] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
Feb 14 18:12:27 debian kernel: [    8.502960] cfg80211:     (5170000 KHz - 5250000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 18:12:27 debian kernel: [    8.502966] cfg80211:     (5250000 KHz - 5330000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 18:12:27 debian kernel: [    8.502972] cfg80211:     (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 18:12:27 debian kernel: [    8.502978] cfg80211:     (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm)
Feb 14 18:12:27 debian kernel: [    8.502985] cfg80211:     (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm)
Feb 14 18:12:27 debian kernel: [    8.513271] Linux media interface: v0.10
Feb 14 18:12:27 debian kernel: [    8.561759] Linux video capture interface: v2.00
Feb 14 18:12:27 debian kernel: [    8.685468] uvcvideo: Found UVC 1.00 device TOSHIBA Web Camera - HD (10f1:1a5b)
Feb 14 18:12:27 debian kernel: [    8.719311] input: TOSHIBA Web Camera - HD as /devices/pci0000:00/0000:00:13.0/usb4/4-1/4-1.2/4-1.2:1.0/input/input12
Feb 14 18:12:27 debian kernel: [    8.719562] usbcore: registered new interface driver uvcvideo
Feb 14 18:12:27 debian kernel: [    8.719568] USB Video Class driver (1.1.1)
Feb 14 18:12:27 debian kernel: [   11.117984] Adding 7300092k swap on /dev/sda3.  Priority:-1 extents:1 across:7300092k 
Feb 14 18:12:27 debian kernel: [   11.153695] EXT4-fs (sda2): re-mounted. Opts: (null)
Feb 14 18:12:27 debian kernel: [   11.384224] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Feb 14 18:12:27 debian kernel: [   11.510703] loop: module loaded
Feb 14 18:12:27 debian kernel: [   12.481905] FAT-fs (sda1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Feb 14 18:12:27 debian kernel: [   12.985963] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 14 18:12:27 debian kernel: [   13.110288] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Feb 14 18:12:27 debian kernel: [   14.203346] RPC: Registered named UNIX socket transport module.
Feb 14 18:12:27 debian kernel: [   14.203355] RPC: Registered udp transport module.
Feb 14 18:12:27 debian kernel: [   14.203359] RPC: Registered tcp transport module.
Feb 14 18:12:27 debian kernel: [   14.203364] RPC: Registered tcp NFSv4.1 backchannel transport module.
Feb 14 18:12:27 debian kernel: [   14.244865] FS-Cache: Loaded
Feb 14 18:12:27 debian kernel: [   14.302212] FS-Cache: Netfs 'nfs' registered for caching
Feb 14 18:12:27 debian kernel: [   14.318555] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Feb 14 18:12:28 debian kernel: [   17.132502] input: ACPI Virtual Keyboard Device as /devices/virtual/input/input13
Feb 14 18:12:29 debian kernel: [   18.922365] Bluetooth: Core ver 2.16
Feb 14 18:12:29 debian kernel: [   18.922425] NET: Registered protocol family 31
Feb 14 18:12:29 debian kernel: [   18.922431] Bluetooth: HCI device and connection manager initialized
Feb 14 18:12:29 debian kernel: [   18.922439] Bluetooth: HCI socket layer initialized
Feb 14 18:12:29 debian kernel: [   18.922445] Bluetooth: L2CAP socket layer initialized
Feb 14 18:12:29 debian kernel: [   18.922460] Bluetooth: SCO socket layer initialized
Feb 14 18:12:30 debian kernel: [   18.937195] Bluetooth: RFCOMM TTY layer initialized
Feb 14 18:12:30 debian kernel: [   18.937209] Bluetooth: RFCOMM socket layer initialized
Feb 14 18:12:30 debian kernel: [   18.937214] Bluetooth: RFCOMM ver 1.11
Feb 14 18:12:30 debian kernel: [   19.069247] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 14 18:12:30 debian kernel: [   19.069255] Bluetooth: BNEP filters: protocol multicast
Feb 14 18:12:30 debian kernel: [   19.758646] lp: driver loaded but no devices found
Feb 14 18:12:30 debian kernel: [   19.924620] ppdev: user-space parallel port driver
Feb 14 18:12:31 debian kernel: [   20.741162] r8169 0000:01:00.0: eth0: link down
Feb 14 18:12:31 debian kernel: [   20.744343] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 14 18:13:24 debian kernel: [   73.322163] IN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:24:d4:ba:0e:bb:08:00 SRC=192.168.0.254 DST=255.255.255.255 LEN=576 TOS=0x00 PREC=0x00 TTL=64 ID=0 PROTO=UDP SPT=67 DPT=68 LEN=556 
Feb 14 18:13:26 debian kernel: [   75.619757] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=402 TOS=0x00 PREC=0x00 TTL=255 ID=44225 DF PROTO=UDP SPT=5353 DPT=5353 LEN=382 
Feb 14 18:13:26 debian kernel: [   75.653488] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=188 TOS=0x00 PREC=0x00 TTL=255 ID=44229 DF PROTO=UDP SPT=5353 DPT=5353 LEN=168 
Feb 14 18:13:26 debian kernel: [   75.870160] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=402 TOS=0x00 PREC=0x00 TTL=255 ID=44232 DF PROTO=UDP SPT=5353 DPT=5353 LEN=382 
Feb 14 18:13:27 debian kernel: [   76.121220] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=402 TOS=0x00 PREC=0x00 TTL=255 ID=44267 DF PROTO=UDP SPT=5353 DPT=5353 LEN=382 
Feb 14 18:13:27 debian kernel: [   76.321400] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=372 TOS=0x00 PREC=0x00 TTL=255 ID=44316 DF PROTO=UDP SPT=5353 DPT=5353 LEN=352 
Feb 14 18:13:27 debian kernel: [   76.812251] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=188 TOS=0x00 PREC=0x00 TTL=255 ID=44346 DF PROTO=UDP SPT=5353 DPT=5353 LEN=168 
Feb 14 18:13:28 debian kernel: [   77.481285] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=372 TOS=0x00 PREC=0x00 TTL=255 ID=44468 DF PROTO=UDP SPT=5353 DPT=5353 LEN=352 
Feb 14 18:13:30 debian kernel: [   78.973618] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=305 TOS=0x00 PREC=0x00 TTL=255 ID=44609 DF PROTO=UDP SPT=5353 DPT=5353 LEN=285 
Feb 14 18:13:30 debian kernel: [   79.640699] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=372 TOS=0x00 PREC=0x00 TTL=255 ID=44687 DF PROTO=UDP SPT=5353 DPT=5353 LEN=352 
Feb 14 18:13:34 debian kernel: [   83.208168] eth1: no IPv6 routers present
Feb 14 18:13:54 debian kernel: [  103.166957] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=628 DF PROTO=UDP SPT=8610 DPT=8612 LEN=24 
Feb 14 18:13:54 debian kernel: [  103.267985] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=637 DF PROTO=UDP SPT=8611 DPT=8612 LEN=24 
Feb 14 18:13:54 debian kernel: [  103.368408] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=644 DF PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Feb 14 18:13:54 debian kernel: [  103.468805] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=646 DF PROTO=UDP SPT=8613 DPT=8612 LEN=24 
Feb 14 18:13:54 debian kernel: [  103.569340] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=660 DF PROTO=UDP SPT=8614 DPT=8612 LEN=24 
Feb 14 18:13:57 debian kernel: [  106.547576] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=255.255.255.255 LEN=43 TOS=0x00 PREC=0x00 TTL=64 ID=17594 DF PROTO=UDP SPT=49578 DPT=3289 LEN=23 
Feb 14 18:13:58 debian kernel: [  107.664443] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=255.255.255.255 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=17672 DF PROTO=UDP SPT=60608 DPT=1124 LEN=45 
Feb 14 18:14:00 debian kernel: [  109.016190] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=47622 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
Feb 14 18:14:00 debian kernel: [  109.439119] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=2017 DF PROTO=UDP SPT=8610 DPT=8612 LEN=24 
Feb 14 18:14:00 debian kernel: [  109.539595] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=2029 DF PROTO=UDP SPT=8611 DPT=8612 LEN=24 
Feb 14 18:14:00 debian kernel: [  109.640169] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=2038 DF PROTO=UDP SPT=8612 DPT=8612 LEN=24 
Feb 14 18:14:00 debian kernel: [  109.740593] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=2041 DF PROTO=UDP SPT=8613 DPT=8612 LEN=24 
Feb 14 18:14:00 debian kernel: [  109.841108] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=192.168.0.255 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=2045 DF PROTO=UDP SPT=8614 DPT=8612 LEN=24 
Feb 14 18:14:01 debian kernel: [  110.477720] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=255.255.255.255 LEN=43 TOS=0x00 PREC=0x00 TTL=64 ID=18129 DF PROTO=UDP SPT=53249 DPT=3289 LEN=23 
Feb 14 18:14:02 debian kernel: [  111.482842] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=255.255.255.255 LEN=65 TOS=0x00 PREC=0x00 TTL=64 ID=18147 DF PROTO=UDP SPT=36861 DPT=1124 LEN=45 
Feb 14 18:14:02 debian kernel: [  111.927735] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=48215 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
Feb 14 18:14:03 debian kernel: [  112.927470] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=48444 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
Feb 14 18:14:06 debian kernel: [  114.929611] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=48668 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
Feb 14 18:14:10 debian kernel: [  118.932774] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=49405 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
Feb 14 18:14:18 debian kernel: [  126.940018] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=51333 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
Feb 14 18:14:34 debian kernel: [  142.956802] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=67 TOS=0x00 PREC=0x00 TTL=255 ID=51550 DF PROTO=UDP SPT=5353 DPT=5353 LEN=47 
Feb 14 18:14:45 debian kernel: [  154.339799] Chrome_ChildThr[4731]: segfault at 0 ip 00007f131363d4aa sp 00007f130b6e04b0 error 6 in libmozalloc.so[7f131363c000+2000]
Feb 14 18:14:47 debian kernel: [  156.219326] IN=eth1 OUT= MAC= SRC=192.168.0.10 DST=224.0.0.251 LEN=451 TOS=0x00 PREC=0x00 TTL=255 ID=53413 DF PROTO=UDP SPT=5353 DPT=5353 LEN=431 
Feb 14 18:14:48 debian kernel: [  156.944110] cfg80211: Calling CRDA to update world regulatory domain
Feb 14 18:14:48 debian kernel: [  156.950679] cfg80211: World regulatory domain updated:
Feb 14 18:14:48 debian kernel: [  156.950685] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 14 18:14:48 debian kernel: [  156.950690] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 18:14:48 debian kernel: [  156.950694] cfg80211:     (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 18:14:48 debian kernel: [  156.950698] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
Feb 14 18:14:48 debian kernel: [  156.950701] cfg80211:     (5170000 KHz - 5250000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 18:14:48 debian kernel: [  156.950705] cfg80211:     (5250000 KHz - 5330000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 18:14:48 debian kernel: [  156.950708] cfg80211:     (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 18:14:48 debian kernel: [  156.950712] cfg80211:     (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm)
Feb 14 18:14:48 debian kernel: [  156.950715] cfg80211:     (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm)
Feb 14 19:32:42 debian kernel: imklog 5.8.11, log source = /proc/kmsg started.
Feb 14 19:32:42 debian kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb 14 19:32:42 debian kernel: [    0.000000] Initializing cgroup subsys cpu
Feb 14 19:32:42 debian kernel: [    0.000000] Linux version 3.2.0-4-amd64 (debian-kernel@lists.debian.org) (gcc version 4.6.3 (Debian 4.6.3-14) ) #1 SMP Debian 3.2.65-1+deb7u1
Feb 14 19:32:42 debian kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-4-amd64 root=UUID=1ba23965-7652-4f10-a52f-41bb82fd7619 ro quiet
Feb 14 19:32:42 debian kernel: [    0.000000] BIOS-provided physical RAM map:
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000006e000 (usable)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 000000000006e000 - 0000000000070000 (ACPI NVS)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 0000000000070000 - 0000000000086000 (usable)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 0000000000086000 - 00000000000c0000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000097c34000 (usable)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 0000000097c34000 - 000000009853c000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 000000009853c000 - 000000009f28f000 (usable)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 000000009f28f000 - 000000009f48f000 type 20
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 000000009f48f000 - 000000009fa8f000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 000000009fa8f000 - 000000009fb8f000 (ACPI NVS)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 000000009fb8f000 - 000000009fbff000 (ACPI data)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 000000009fbff000 - 000000009fc00000 (usable)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 000000009fc00000 - 00000000e0000000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 00000000f2800000 - 00000000f2900000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec02000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 00000000fec10000 - 00000000fec11000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 00000000fed80000 - 00000000fed81000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000021f000000 (usable)
Feb 14 19:32:42 debian kernel: [    0.000000] NX (Execute Disable) protection: active
Feb 14 19:32:42 debian kernel: [    0.000000] EFI v2.31 by INSYDE Corp.
Feb 14 19:32:42 debian kernel: [    0.000000]  ACPI=0x9fbfe000  ACPI 2.0=0x9fbfe014  SMBIOS=0x9fa8ef98 
Feb 14 19:32:42 debian kernel: [    0.000000] Kernel-defined memdesc doesn't match the one from EFI!
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem01: type=7, attr=0xf, range=[0x0000000000001000-0x000000000006e000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem02: type=10, attr=0xf, range=[0x000000000006e000-0x0000000000070000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem03: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000086000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem04: type=0, attr=0xf, range=[0x0000000000086000-0x0000000000088000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem05: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x00000000000a0000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem06: type=2, attr=0xf, range=[0x0000000000100000-0x0000000000c54000) (11MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem07: type=7, attr=0xf, range=[0x0000000000c54000-0x0000000036a6a000) (862MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem08: type=2, attr=0xf, range=[0x0000000036a6a000-0x000000003752d000) (10MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem09: type=7, attr=0xf, range=[0x000000003752d000-0x000000006eddf000) (888MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem10: type=2, attr=0xf, range=[0x000000006eddf000-0x0000000095540000) (615MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem11: type=4, attr=0xf, range=[0x0000000095540000-0x0000000095560000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem12: type=7, attr=0xf, range=[0x0000000095560000-0x00000000967a8000) (18MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem13: type=2, attr=0xf, range=[0x00000000967a8000-0x0000000096895000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem14: type=7, attr=0xf, range=[0x0000000096895000-0x0000000096896000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem15: type=2, attr=0xf, range=[0x0000000096896000-0x0000000096897000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem16: type=7, attr=0xf, range=[0x0000000096897000-0x0000000096898000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem17: type=2, attr=0xf, range=[0x0000000096898000-0x000000009689d000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem18: type=7, attr=0xf, range=[0x000000009689d000-0x00000000968a1000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem19: type=2, attr=0xf, range=[0x00000000968a1000-0x00000000968a3000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem20: type=7, attr=0xf, range=[0x00000000968a3000-0x00000000968a5000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem21: type=2, attr=0xf, range=[0x00000000968a5000-0x00000000968a6000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem22: type=7, attr=0xf, range=[0x00000000968a6000-0x00000000968a7000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem23: type=2, attr=0xf, range=[0x00000000968a7000-0x00000000968a8000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem24: type=7, attr=0xf, range=[0x00000000968a8000-0x00000000968a9000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem25: type=2, attr=0xf, range=[0x00000000968a9000-0x00000000968aa000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem26: type=7, attr=0xf, range=[0x00000000968aa000-0x00000000968ac000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem27: type=2, attr=0xf, range=[0x00000000968ac000-0x0000000096996000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem28: type=4, attr=0xf, range=[0x0000000096996000-0x0000000097c34000) (18MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem29: type=0, attr=0xf, range=[0x0000000097c34000-0x000000009853c000) (9MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem30: type=2, attr=0xf, range=[0x000000009853c000-0x000000009853f000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem31: type=7, attr=0xf, range=[0x000000009853f000-0x000000009861c000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem32: type=1, attr=0xf, range=[0x000000009861c000-0x000000009873f000) (1MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem33: type=7, attr=0xf, range=[0x000000009873f000-0x000000009bb84000) (52MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem34: type=4, attr=0xf, range=[0x000000009bb84000-0x000000009bb9b000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem35: type=7, attr=0xf, range=[0x000000009bb9b000-0x000000009bbb9000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem36: type=4, attr=0xf, range=[0x000000009bbb9000-0x000000009bcba000) (1MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem37: type=7, attr=0xf, range=[0x000000009bcba000-0x000000009bcbb000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem38: type=4, attr=0xf, range=[0x000000009bcbb000-0x000000009c200000) (5MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem39: type=7, attr=0xf, range=[0x000000009c200000-0x000000009c201000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem40: type=4, attr=0xf, range=[0x000000009c201000-0x000000009ca0e000) (8MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem41: type=7, attr=0xf, range=[0x000000009ca0e000-0x000000009ca11000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem42: type=4, attr=0xf, range=[0x000000009ca11000-0x000000009ca19000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem43: type=7, attr=0xf, range=[0x000000009ca19000-0x000000009ca1c000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem44: type=4, attr=0xf, range=[0x000000009ca1c000-0x000000009ec8f000) (34MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem45: type=7, attr=0xf, range=[0x000000009ec8f000-0x000000009ee36000) (1MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem46: type=2, attr=0xf, range=[0x000000009ee36000-0x000000009ee40000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem47: type=3, attr=0xf, range=[0x000000009ee40000-0x000000009f28f000) (4MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem48: type=5, attr=0x800000000000000f, range=[0x000000009f28f000-0x000000009f48f000) (2MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem49: type=6, attr=0x800000000000000f, range=[0x000000009f48f000-0x000000009f68f000) (2MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem50: type=0, attr=0xf, range=[0x000000009f68f000-0x000000009fa8f000) (4MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem51: type=10, attr=0xf, range=[0x000000009fa8f000-0x000000009fb8f000) (1MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem52: type=9, attr=0xf, range=[0x000000009fb8f000-0x000000009fbff000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem53: type=4, attr=0xf, range=[0x000000009fbff000-0x000000009fc00000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem54: type=7, attr=0xf, range=[0x0000000100000000-0x000000021f000000) (4592MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem55: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem56: type=0, attr=0x0, range=[0x000000009fc00000-0x00000000e0000000) (1028MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem57: type=11, attr=0x8000000000000000, range=[0x00000000f2800000-0x00000000f2900000) (1MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem58: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem59: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec02000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem60: type=11, attr=0x8000000000000001, range=[0x00000000fec10000-0x00000000fec11000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem61: type=11, attr=0x8000000000000001, range=[0x00000000fed80000-0x00000000fed81000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem62: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
Feb 14 19:32:42 debian kernel: [    0.000000] EFI: mem63: type=11, attr=0x8000000000000000, range=[0x00000000ff800000-0x0000000100000000) (8MB)
Feb 14 19:32:42 debian kernel: [    0.000000] SMBIOS 2.8 present.
Feb 14 19:32:42 debian kernel: [    0.000000] DMI: TOSHIBA SATELLITE C70D-B/Portable PC, BIOS 1.30 08/14/2014
Feb 14 19:32:42 debian kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Feb 14 19:32:42 debian kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Feb 14 19:32:42 debian kernel: [    0.000000] No AGP bridge found
Feb 14 19:32:42 debian kernel: [    0.000000] last_pfn = 0x21f000 max_arch_pfn = 0x400000000
Feb 14 19:32:42 debian kernel: [    0.000000] MTRR default type: uncachable
Feb 14 19:32:42 debian kernel: [    0.000000] MTRR fixed ranges enabled:
Feb 14 19:32:42 debian kernel: [    0.000000]   00000-9FFFF write-back
Feb 14 19:32:42 debian kernel: [    0.000000]   A0000-BFFFF uncachable
Feb 14 19:32:42 debian kernel: [    0.000000]   C0000-FFFFF write-through
Feb 14 19:32:42 debian kernel: [    0.000000] MTRR variable ranges enabled:
Feb 14 19:32:42 debian kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Feb 14 19:32:42 debian kernel: [    0.000000]   1 base 0080000000 mask FFE0000000 write-back
Feb 14 19:32:42 debian kernel: [    0.000000]   2 base 009FB78000 mask FFFFFFF000 uncachable
Feb 14 19:32:42 debian kernel: [    0.000000]   3 base 00FF800000 mask FFFF800000 write-protect
Feb 14 19:32:42 debian kernel: [    0.000000]   4 disabled
Feb 14 19:32:42 debian kernel: [    0.000000]   5 disabled
Feb 14 19:32:42 debian kernel: [    0.000000]   6 disabled
Feb 14 19:32:42 debian kernel: [    0.000000]   7 disabled
Feb 14 19:32:42 debian kernel: [    0.000000] TOM2: 000000021f000000 aka 8688M
Feb 14 19:32:42 debian kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Feb 14 19:32:42 debian kernel: [    0.000000] last_pfn = 0x9fc00 max_arch_pfn = 0x400000000
Feb 14 19:32:42 debian kernel: [    0.000000] initial memory mapped : 0 - 20000000
Feb 14 19:32:42 debian kernel: [    0.000000] Base memory trampoline at [ffff88000007d000] 7d000 size 20480
Feb 14 19:32:42 debian kernel: [    0.000000] Using GB pages for direct mapping
Feb 14 19:32:42 debian kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000009fc00000
Feb 14 19:32:42 debian kernel: [    0.000000]  0000000000 - 0080000000 page 1G
Feb 14 19:32:42 debian kernel: [    0.000000]  0080000000 - 009fc00000 page 2M
Feb 14 19:32:42 debian kernel: [    0.000000] kernel direct mapping tables up to 9fc00000 @ 1fffe000-20000000
Feb 14 19:32:42 debian kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000021f000000
Feb 14 19:32:42 debian kernel: [    0.000000]  0100000000 - 0200000000 page 1G
Feb 14 19:32:42 debian kernel: [    0.000000]  0200000000 - 021f000000 page 2M
Feb 14 19:32:42 debian kernel: [    0.000000] kernel direct mapping tables up to 21f000000 @ 9ee3e000-9ee40000
Feb 14 19:32:42 debian kernel: [    0.000000] RAMDISK: 36a6a000 - 3752d000
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: RSDP 000000009fbfe014 00024 (v02 TOSINV)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: XSDT 000000009fbc7188 000D4 (v01 TOSINV TOSINV00 00000001      01000013)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: FACP 000000009fbfc000 0010C (v05 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI Warning: FADT (revision 5) is longer than ACPI 2.0 version, truncating length 268 to 244 (20110623/tbfadt-288)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: DSDT 000000009fbf2000 05F3F (v01 TOSINV TOSINV00 F0000000 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: FACS 000000009fb2f000 00040
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: UEFI 000000009fbfd000 00236 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: HPET 000000009fbfb000 00038 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: APIC 000000009fbfa000 00090 (v03 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: MCFG 000000009fbf9000 0003C (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: ASF! 000000009fbf8000 000A5 (v32 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: BOOT 000000009fbf1000 00028 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SLIC 000000009fbf0000 00176 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: FPDT 000000009fbee000 00044 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: MSDM 000000009fbed000 00055 (v03 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbe6000 06D71 (v01 TOSINV   TsbOdm 00001000 INTL 20120215)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbe5000 00CB0 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbe0000 0487A (v02 TOSINV TOSINV00 00000002 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: VFCT 000000009fbd1000 0EC84 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbd0000 0085A (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbcf000 00418 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbcd000 01309 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbcc000 0008C (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbca000 01138 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: SSDT 000000009fbc8000 00FB4 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: WPBT 000000009fbbe000 00038 (v01 TOSINV TOSINV00 00000001 ABTW 20120402)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: BGRT 000000009fbc9000 00038 (v01 TOSINV TOSINV00 00000001 ACPI 00040000)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 14 19:32:42 debian kernel: [    0.000000] No NUMA configuration found
Feb 14 19:32:42 debian kernel: [    0.000000] Faking a node at 0000000000000000-000000021f000000
Feb 14 19:32:42 debian kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000021f000000
Feb 14 19:32:42 debian kernel: [    0.000000]   NODE_DATA [000000021effb000 - 000000021effffff]
Feb 14 19:32:42 debian kernel: [    0.000000]  [ffffea0000000000-ffffea00077fffff] PMD -> [ffff880217600000-ffff88021d9fffff] on node 0
Feb 14 19:32:42 debian kernel: [    0.000000] Zone PFN ranges:
Feb 14 19:32:42 debian kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Feb 14 19:32:42 debian kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Feb 14 19:32:42 debian kernel: [    0.000000]   Normal   0x00100000 -> 0x0021f000
Feb 14 19:32:42 debian kernel: [    0.000000] Movable zone start PFN for each node
Feb 14 19:32:42 debian kernel: [    0.000000] early_node_map[6] active PFN ranges
Feb 14 19:32:42 debian kernel: [    0.000000]     0: 0x00000010 -> 0x0000006e
Feb 14 19:32:42 debian kernel: [    0.000000]     0: 0x00000070 -> 0x00000086
Feb 14 19:32:42 debian kernel: [    0.000000]     0: 0x00000100 -> 0x00097c34
Feb 14 19:32:42 debian kernel: [    0.000000]     0: 0x0009853c -> 0x0009f28f
Feb 14 19:32:42 debian kernel: [    0.000000]     0: 0x0009fbff -> 0x0009fc00
Feb 14 19:32:42 debian kernel: [    0.000000]     0: 0x00100000 -> 0x0021f000
Feb 14 19:32:42 debian kernel: [    0.000000] On node 0 totalpages: 1825020
Feb 14 19:32:42 debian kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Feb 14 19:32:42 debian kernel: [    0.000000]   DMA zone: 6 pages reserved
Feb 14 19:32:42 debian kernel: [    0.000000]   DMA zone: 3894 pages, LIFO batch:0
Feb 14 19:32:42 debian kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Feb 14 19:32:42 debian kernel: [    0.000000]   DMA32 zone: 631232 pages, LIFO batch:31
Feb 14 19:32:42 debian kernel: [    0.000000]   Normal zone: 16072 pages used for memmap
Feb 14 19:32:42 debian kernel: [    0.000000]   Normal zone: 1159480 pages, LIFO batch:31
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Feb 14 19:32:42 debian kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec01000] gsi_base[24])
Feb 14 19:32:42 debian kernel: [    0.000000] IOAPIC[1]: apic_id 5, version 33, address 0xfec01000, GSI 24-55
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: IRQ0 used by override.
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: IRQ2 used by override.
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: IRQ9 used by override.
Feb 14 19:32:42 debian kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Feb 14 19:32:42 debian kernel: [    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
Feb 14 19:32:42 debian kernel: [    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
Feb 14 19:32:42 debian kernel: [    0.000000] nr_irqs_gsi: 72
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 000000000006e000 - 0000000000070000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 0000000000086000 - 00000000000c0000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 0000000097c34000 - 000000009853c000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009f28f000 - 000000009f48f000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009f48f000 - 000000009fa8f000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009fa8f000 - 000000009fb8f000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009fb8f000 - 000000009fbff000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 000000009fc00000 - 00000000e0000000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f2800000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000f2800000 - 00000000f2900000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000f2900000 - 00000000f8000000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec02000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fec02000 - 00000000fec10000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fec11000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fec11000 - 00000000fed80000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fed80000 - 00000000fed81000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fed81000 - 00000000fee00000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ff800000
Feb 14 19:32:42 debian kernel: [    0.000000] PM: Registered nosave memory: 00000000ff800000 - 0000000100000000
Feb 14 19:32:42 debian kernel: [    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:12800000)
Feb 14 19:32:42 debian kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Feb 14 19:32:42 debian kernel: [    0.000000] setup_percpu: NR_CPUS:512 nr_cpumask_bits:512 nr_cpu_ids:4 nr_node_ids:1
Feb 14 19:32:42 debian kernel: [    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88021ec00000 s78848 r8192 d23552 u524288
Feb 14 19:32:42 debian kernel: [    0.000000] pcpu-alloc: s78848 r8192 d23552 u524288 alloc=1*2097152
Feb 14 19:32:42 debian kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Feb 14 19:32:42 debian kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1794606
Feb 14 19:32:42 debian kernel: [    0.000000] Policy zone: Normal
Feb 14 19:32:42 debian kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-4-amd64 root=UUID=1ba23965-7652-4f10-a52f-41bb82fd7619 ro quiet
Feb 14 19:32:42 debian kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Feb 14 19:32:42 debian kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
Feb 14 19:32:42 debian kernel: [    0.000000] Checking aperture...
Feb 14 19:32:42 debian kernel: [    0.000000] No AGP bridge found
Feb 14 19:32:42 debian kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Feb 14 19:32:42 debian kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Feb 14 19:32:42 debian kernel: [    0.000000] Memory: 7037968k/8896512k available (3433k kernel code, 1596432k absent, 262112k reserved, 3305k data, 576k init)
Feb 14 19:32:42 debian kernel: [    0.000000] Hierarchical RCU implementation.
Feb 14 19:32:42 debian kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Feb 14 19:32:42 debian kernel: [    0.000000] NR_IRQS:33024 nr_irqs:1024 16
Feb 14 19:32:42 debian kernel: [    0.000000] Console: colour dummy device 80x25
Feb 14 19:32:42 debian kernel: [    0.000000] console [tty0] enabled
Feb 14 19:32:42 debian kernel: [    0.000000] hpet clockevent registered
Feb 14 19:32:42 debian kernel: [    0.000000] Fast TSC calibration using PIT
Feb 14 19:32:42 debian kernel: [    0.000000] Detected 1996.542 MHz processor.
Feb 14 19:32:42 debian kernel: [    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 3993.08 BogoMIPS (lpj=7986168)
Feb 14 19:32:42 debian kernel: [    0.004012] pid_max: default: 32768 minimum: 301
Feb 14 19:32:42 debian kernel: [    0.028134] Security Framework initialized
Feb 14 19:32:42 debian kernel: [    0.028150] AppArmor: AppArmor disabled by boot time parameter
Feb 14 19:32:42 debian kernel: [    0.032534] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Feb 14 19:32:42 debian kernel: [    0.037425] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Feb 14 19:32:42 debian kernel: [    0.039928] Mount-cache hash table entries: 256
Feb 14 19:32:42 debian kernel: [    0.040192] Initializing cgroup subsys cpuacct
Feb 14 19:32:42 debian kernel: [    0.040199] Initializing cgroup subsys memory
Feb 14 19:32:42 debian kernel: [    0.040220] Initializing cgroup subsys devices
Feb 14 19:32:42 debian kernel: [    0.040223] Initializing cgroup subsys freezer
Feb 14 19:32:42 debian kernel: [    0.040227] Initializing cgroup subsys net_cls
Feb 14 19:32:42 debian kernel: [    0.040230] Initializing cgroup subsys blkio
Feb 14 19:32:42 debian kernel: [    0.040241] Initializing cgroup subsys perf_event
Feb 14 19:32:42 debian kernel: [    0.040291] tseg: 009fc00000
Feb 14 19:32:42 debian kernel: [    0.040294] CPU: Physical Processor ID: 0
Feb 14 19:32:42 debian kernel: [    0.040296] CPU: Processor Core ID: 0
Feb 14 19:32:42 debian kernel: [    0.049429] mce: CPU supports 6 MCE banks
Feb 14 19:32:42 debian kernel: [    0.050066] ACPI: Core revision 20110623
Feb 14 19:32:42 debian kernel: [    0.064684] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Feb 14 19:32:42 debian kernel: [    0.104547] CPU0: AMD A8-6410 APU with AMD Radeon R5 Graphics     stepping 01
Feb 14 19:32:42 debian kernel: [    0.108005] Performance Events: AMD PMU driver.
Feb 14 19:32:42 debian kernel: [    0.108005] ... version:                0
Feb 14 19:32:42 debian kernel: [    0.108005] ... bit width:              48
Feb 14 19:32:42 debian kernel: [    0.108005] ... generic registers:      4
Feb 14 19:32:42 debian kernel: [    0.108005] ... value mask:             0000ffffffffffff
Feb 14 19:32:42 debian kernel: [    0.108005] ... max period:             00007fffffffffff
Feb 14 19:32:42 debian kernel: [    0.108005] ... fixed-purpose events:   0
Feb 14 19:32:42 debian kernel: [    0.108005] ... event mask:             000000000000000f
Feb 14 19:32:42 debian kernel: [    0.108005] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 19:32:42 debian kernel: [    0.108005] Booting Node   0, Processors  #1
Feb 14 19:32:42 debian kernel: [    0.108005] smpboot cpu 1: start_ip = 7d000
Feb 14 19:32:42 debian kernel: [    0.204080] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 19:32:42 debian kernel: [    0.204356]  #2
Feb 14 19:32:42 debian kernel: [    0.204359] smpboot cpu 2: start_ip = 7d000
Feb 14 19:32:42 debian kernel: [    0.308088] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 19:32:42 debian kernel: [    0.308359]  #3 Ok.
Feb 14 19:32:42 debian kernel: [    0.308361] smpboot cpu 3: start_ip = 7d000
Feb 14 19:32:42 debian kernel: [    0.412102] NMI watchdog enabled, takes one hw-pmu counter.
Feb 14 19:32:42 debian kernel: [    0.412187] Brought up 4 CPUs
Feb 14 19:32:42 debian kernel: [    0.412190] Total of 4 processors activated (15969.65 BogoMIPS).
Feb 14 19:32:42 debian kernel: [    0.413484] devtmpfs: initialized
Feb 14 19:32:42 debian kernel: [    0.418689] PM: Registering ACPI NVS region at 6e000 (8192 bytes)
Feb 14 19:32:42 debian kernel: [    0.418689] PM: Registering ACPI NVS region at 9fa8f000 (1048576 bytes)
Feb 14 19:32:42 debian kernel: [    0.418689] print_constraints: dummy: 
Feb 14 19:32:42 debian kernel: [    0.418689] NET: Registered protocol family 16
Feb 14 19:32:42 debian kernel: [    0.418689] Extended Config Space enabled on 0 nodes
Feb 14 19:32:42 debian kernel: [    0.418689] ACPI: bus type pci registered
Feb 14 19:32:42 debian kernel: [    0.418689] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
Feb 14 19:32:42 debian kernel: [    0.418689] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
Feb 14 19:32:42 debian kernel: [    0.425181] PCI: Using configuration type 1 for base access
Feb 14 19:32:42 debian kernel: [    0.426261] bio: create slab <bio-0> at 0
Feb 14 19:32:42 debian kernel: [    0.426261] ACPI: Added _OSI(Module Device)
Feb 14 19:32:42 debian kernel: [    0.426261] ACPI: Added _OSI(Processor Device)
Feb 14 19:32:42 debian kernel: [    0.426261] ACPI: Added _OSI(3.0 _SCP Extensions)
Feb 14 19:32:42 debian kernel: [    0.426261] ACPI: Added _OSI(Processor Aggregator Device)
Feb 14 19:32:42 debian kernel: [    0.428791] ACPI: EC: Look up EC in DSDT
Feb 14 19:32:42 debian kernel: [    0.431114] ACPI: Executed 1 blocks of module-level executable AML code
Feb 14 19:32:42 debian kernel: [    0.456343] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Feb 14 19:32:42 debian kernel: [    0.650126] ACPI: Interpreter enabled
Feb 14 19:32:42 debian kernel: [    0.650134] ACPI: (supports S0 S3 S4 S5)
Feb 14 19:32:42 debian kernel: [    0.650163] ACPI: Using IOAPIC for interrupt routing
Feb 14 19:32:42 debian kernel: [    0.867408] ACPI: Power Resource [PFA1] (off)
Feb 14 19:32:42 debian kernel: [    0.956214] ACPI: No dock devices found.
Feb 14 19:32:42 debian kernel: [    0.956214] HEST: Table not found.
Feb 14 19:32:42 debian kernel: [    0.956214] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Feb 14 19:32:42 debian kernel: [    0.996255] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0xe0000000-0xf7ffffff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0xfc000000-0xfed3ffff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci_root PNP0A08:00: host bridge window [mem 0xfed45000-0xffffffff]
Feb 14 19:32:42 debian kernel: [    1.016332] pci 0000:00:00.0: [1022:1566] type 0 class 0x000600
Feb 14 19:32:42 debian kernel: [    1.016332] pci 0000:00:01.0: [1002:9851] type 0 class 0x000300
Feb 14 19:32:42 debian kernel: [    1.016332] pci 0000:00:01.0: reg 10: [mem 0xe0000000-0xefffffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.016332] pci 0000:00:01.0: reg 18: [mem 0xf2000000-0xf27fffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.016334] pci 0000:00:01.0: reg 20: [io  0x3000-0x30ff]
Feb 14 19:32:42 debian kernel: [    1.016341] pci 0000:00:01.0: reg 24: [mem 0xf2c00000-0xf2c3ffff]
Feb 14 19:32:42 debian kernel: [    1.016347] pci 0000:00:01.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Feb 14 19:32:42 debian kernel: [    1.016379] pci 0000:00:01.0: supports D1 D2
Feb 14 19:32:42 debian kernel: [    1.016382] pci 0000:00:01.0: PME# supported from D1 D2 D3hot
Feb 14 19:32:42 debian kernel: [    1.016406] pci 0000:00:01.1: [1002:9840] type 0 class 0x000403
Feb 14 19:32:42 debian kernel: [    1.016417] pci 0000:00:01.1: reg 10: [mem 0xf2c60000-0xf2c63fff 64bit]
Feb 14 19:32:42 debian kernel: [    1.016468] pci 0000:00:01.1: supports D1 D2
Feb 14 19:32:42 debian kernel: [    1.016488] pci 0000:00:02.0: [1022:156b] type 0 class 0x000600
Feb 14 19:32:42 debian kernel: [    1.016522] pci 0000:00:02.2: [1022:1439] type 1 class 0x000604
Feb 14 19:32:42 debian kernel: [    1.016580] pci 0000:00:02.2: PME# supported from D0 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.016604] pci 0000:00:02.3: [1022:1439] type 1 class 0x000604
Feb 14 19:32:42 debian kernel: [    1.016662] pci 0000:00:02.3: PME# supported from D0 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:02.4: [1022:1439] type 1 class 0x000604
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:02.4: PME# supported from D0 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:08.0: [1022:1537] type 0 class 0x001080
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:08.0: reg 10: [mem 0xf2c40000-0xf2c5ffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:08.0: reg 18: [mem 0xf2900000-0xf29fffff]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:08.0: reg 1c: [mem 0xf2c6f000-0xf2c6ffff]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:08.0: reg 24: [mem 0xf2c6a000-0xf2c6bfff]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:10.0: [1022:7814] type 0 class 0x000c03
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:10.0: reg 10: [mem 0xf2c68000-0xf2c69fff 64bit]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:11.0: [1022:7801] type 0 class 0x000106
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:11.0: reg 10: [io  0x3118-0x311f]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:11.0: reg 14: [io  0x3124-0x3127]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:11.0: reg 18: [io  0x3110-0x3117]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:11.0: reg 1c: [io  0x3120-0x3123]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:11.0: reg 20: [io  0x3100-0x310f]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:11.0: reg 24: [mem 0xf2c6e000-0xf2c6e3ff]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:11.0: PME# supported from D3hot
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:12.0: [1022:7808] type 0 class 0x000c03
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:12.0: reg 10: [mem 0xf2c6d000-0xf2c6d0ff]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:12.0: supports D1 D2
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:13.0: [1022:7808] type 0 class 0x000c03
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:13.0: reg 10: [mem 0xf2c6c000-0xf2c6c0ff]
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:13.0: supports D1 D2
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:13.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.016686] pci 0000:00:14.0: [1022:780b] type 0 class 0x000c05
Feb 14 19:32:42 debian kernel: [    1.016729] pci 0000:00:14.2: [1022:780d] type 0 class 0x000403
Feb 14 19:32:42 debian kernel: [    1.016748] pci 0000:00:14.2: reg 10: [mem 0xf2c64000-0xf2c67fff 64bit]
Feb 14 19:32:42 debian kernel: [    1.016805] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.016822] pci 0000:00:14.3: [1022:780e] type 0 class 0x000601
Feb 14 19:32:42 debian kernel: [    1.016890] pci 0000:00:18.0: [1022:1580] type 0 class 0x000600
Feb 14 19:32:42 debian kernel: [    1.016913] pci 0000:00:18.1: [1022:1581] type 0 class 0x000600
Feb 14 19:32:42 debian kernel: [    1.016934] pci 0000:00:18.2: [1022:1582] type 0 class 0x000600
Feb 14 19:32:42 debian kernel: [    1.016956] pci 0000:00:18.3: [1022:1583] type 0 class 0x000600
Feb 14 19:32:42 debian kernel: [    1.016982] pci 0000:00:18.4: [1022:1584] type 0 class 0x000600
Feb 14 19:32:42 debian kernel: [    1.017003] pci 0000:00:18.5: [1022:1585] type 0 class 0x000600
Feb 14 19:32:42 debian kernel: [    1.017081] pci 0000:01:00.0: [10ec:8136] type 0 class 0x000200
Feb 14 19:32:42 debian kernel: [    1.017097] pci 0000:01:00.0: reg 10: [io  0x2000-0x20ff]
Feb 14 19:32:42 debian kernel: [    1.017121] pci 0000:01:00.0: reg 18: [mem 0xf1000000-0xf1000fff 64bit]
Feb 14 19:32:42 debian kernel: [    1.017137] pci 0000:01:00.0: reg 20: [mem 0xf0000000-0xf0003fff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.017201] pci 0000:01:00.0: supports D1 D2
Feb 14 19:32:42 debian kernel: [    1.017203] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.024129] pci 0000:00:02.2: PCI bridge to [bus 01-04]
Feb 14 19:32:42 debian kernel: [    1.024138] pci 0000:00:02.2:   bridge window [io  0x2000-0x2fff]
Feb 14 19:32:42 debian kernel: [    1.024142] pci 0000:00:02.2:   bridge window [mem 0xf1000000-0xf1ffffff]
Feb 14 19:32:42 debian kernel: [    1.024148] pci 0000:00:02.2:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.024244] pci 0000:05:00.0: [14e4:4365] type 0 class 0x000280
Feb 14 19:32:42 debian kernel: [    1.024269] pci 0000:05:00.0: reg 10: [mem 0xf2b00000-0xf2b07fff 64bit]
Feb 14 19:32:42 debian kernel: [    1.024383] pci 0000:05:00.0: supports D1 D2
Feb 14 19:32:42 debian kernel: [    1.024385] pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
Feb 14 19:32:42 debian kernel: [    1.032152] pci 0000:00:02.3: PCI bridge to [bus 05-05]
Feb 14 19:32:42 debian kernel: [    1.032162] pci 0000:00:02.3:   bridge window [mem 0xf2b00000-0xf2bfffff]
Feb 14 19:32:42 debian kernel: [    1.032240] pci 0000:06:00.0: [10ec:5229] type 0 class 0x00ff00
Feb 14 19:32:42 debian kernel: [    1.032260] pci 0000:06:00.0: reg 10: [mem 0xf2a00000-0xf2a00fff]
Feb 14 19:32:42 debian kernel: [    1.032370] pci 0000:06:00.0: supports D1 D2
Feb 14 19:32:42 debian kernel: [    1.032373] pci 0000:06:00.0: PME# supported from D1 D2 D3hot
Feb 14 19:32:42 debian kernel: [    1.040130] pci 0000:00:02.4: PCI bridge to [bus 06-06]
Feb 14 19:32:42 debian kernel: [    1.040141] pci 0000:00:02.4:   bridge window [mem 0xf2a00000-0xf2afffff]
Feb 14 19:32:42 debian kernel: [    1.060129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Feb 14 19:32:42 debian kernel: [    1.080149] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GPP0._PRT]
Feb 14 19:32:42 debian kernel: [    1.080203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GPP1._PRT]
Feb 14 19:32:42 debian kernel: [    1.080278] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.GPP2._PRT]
Feb 14 19:32:42 debian kernel: [    1.080403]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Feb 14 19:32:42 debian kernel: [    1.080409]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Feb 14 19:32:42 debian kernel: [    1.080411] ACPI _OSC control for PCIe not granted, disabling ASPM
Feb 14 19:32:42 debian kernel: [    1.086958] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 19:32:42 debian kernel: [    1.087051] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 19:32:42 debian kernel: [    1.087159] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 19:32:42 debian kernel: [    1.087264] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 19:32:42 debian kernel: [    1.087352] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 19:32:42 debian kernel: [    1.087419] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 19:32:42 debian kernel: [    1.087485] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 19:32:42 debian kernel: [    1.087551] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
Feb 14 19:32:42 debian kernel: [    1.088096] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
Feb 14 19:32:42 debian kernel: [    1.088113] vgaarb: loaded
Feb 14 19:32:42 debian kernel: [    1.088115] vgaarb: bridge control possible 0000:00:01.0
Feb 14 19:32:42 debian kernel: [    1.088186] PCI: Using ACPI for IRQ routing
Feb 14 19:32:42 debian kernel: [    1.089401] PCI: pci_cache_line_size set to 64 bytes
Feb 14 19:32:42 debian kernel: [    1.089515] reserve RAM buffer: 000000000006e000 - 000000000006ffff 
Feb 14 19:32:42 debian kernel: [    1.089519] reserve RAM buffer: 0000000000086000 - 000000000008ffff 
Feb 14 19:32:42 debian kernel: [    1.089522] reserve RAM buffer: 0000000097c34000 - 0000000097ffffff 
Feb 14 19:32:42 debian kernel: [    1.089524] reserve RAM buffer: 000000009f28f000 - 000000009fffffff 
Feb 14 19:32:42 debian kernel: [    1.089528] reserve RAM buffer: 000000009fc00000 - 000000009fffffff 
Feb 14 19:32:42 debian kernel: [    1.089530] reserve RAM buffer: 000000021f000000 - 000000021fffffff 
Feb 14 19:32:42 debian kernel: [    1.089699] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Feb 14 19:32:42 debian kernel: [    1.089705] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Feb 14 19:32:42 debian kernel: [    1.091726] Switching to clocksource hpet
Feb 14 19:32:42 debian kernel: [    1.094445] pnp: PnP ACPI init
Feb 14 19:32:42 debian kernel: [    1.094469] ACPI: bus type pnp registered
Feb 14 19:32:42 debian kernel: [    1.094659] pnp 00:00: [bus 00-ff]
Feb 14 19:32:42 debian kernel: [    1.094663] pnp 00:00: [io  0x0000-0x0cf7 window]
Feb 14 19:32:42 debian kernel: [    1.094666] pnp 00:00: [io  0x0d00-0xffff window]
Feb 14 19:32:42 debian kernel: [    1.094669] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Feb 14 19:32:42 debian kernel: [    1.094672] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
Feb 14 19:32:42 debian kernel: [    1.094675] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
Feb 14 19:32:42 debian kernel: [    1.094678] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
Feb 14 19:32:42 debian kernel: [    1.094680] pnp 00:00: [mem 0x000cc000-0x000cffff window]
Feb 14 19:32:42 debian kernel: [    1.094683] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
Feb 14 19:32:42 debian kernel: [    1.094686] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
Feb 14 19:32:42 debian kernel: [    1.094688] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
Feb 14 19:32:42 debian kernel: [    1.094691] pnp 00:00: [mem 0x000dc000-0x000dffff window]
Feb 14 19:32:42 debian kernel: [    1.094694] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
Feb 14 19:32:42 debian kernel: [    1.094696] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
Feb 14 19:32:42 debian kernel: [    1.094699] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
Feb 14 19:32:42 debian kernel: [    1.094702] pnp 00:00: [mem 0x000ec000-0x000effff window]
Feb 14 19:32:42 debian kernel: [    1.094704] pnp 00:00: [mem 0xe0000000-0xf7ffffff window]
Feb 14 19:32:42 debian kernel: [    1.094707] pnp 00:00: [mem 0xfc000000-0xfed3ffff window]
Feb 14 19:32:42 debian kernel: [    1.094710] pnp 00:00: [mem 0xfed45000-0xffffffff window]
Feb 14 19:32:42 debian kernel: [    1.094712] pnp 00:00: [io  0x0cf8-0x0cff]
Feb 14 19:32:42 debian kernel: [    1.094792] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Feb 14 19:32:42 debian kernel: [    1.094883] pnp 00:01: [mem 0xfec00000-0xfec01fff]
Feb 14 19:32:42 debian kernel: [    1.094886] pnp 00:01: [mem 0xfee00000-0xfee00fff]
Feb 14 19:32:42 debian kernel: [    1.094953] system 00:01: [mem 0xfec00000-0xfec01fff] could not be reserved
Feb 14 19:32:42 debian kernel: [    1.094957] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
Feb 14 19:32:42 debian kernel: [    1.094961] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 14 19:32:42 debian kernel: [    1.095094] pnp 00:02: [irq 0 disabled]
Feb 14 19:32:42 debian kernel: [    1.095107] pnp 00:02: [irq 8]
Feb 14 19:32:42 debian kernel: [    1.095109] pnp 00:02: [mem 0xfed00000-0xfed003ff]
Feb 14 19:32:42 debian kernel: [    1.095148] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
Feb 14 19:32:42 debian kernel: [    1.095226] pnp 00:03: [io  0x0000-0x000f]
Feb 14 19:32:42 debian kernel: [    1.095229] pnp 00:03: [io  0x0081-0x008f]
Feb 14 19:32:42 debian kernel: [    1.095232] pnp 00:03: [io  0x00c0-0x00df]
Feb 14 19:32:42 debian kernel: [    1.095234] pnp 00:03: [dma 4]
Feb 14 19:32:42 debian kernel: [    1.095284] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Feb 14 19:32:42 debian kernel: [    1.095299] pnp 00:04: [io  0x00f0-0x00fe]
Feb 14 19:32:42 debian kernel: [    1.095306] pnp 00:04: [irq 13]
Feb 14 19:32:42 debian kernel: [    1.095347] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Feb 14 19:32:42 debian kernel: [    1.095388] pnp 00:05: [io  0x0070-0x0071]
Feb 14 19:32:42 debian kernel: [    1.095432] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
Feb 14 19:32:42 debian kernel: [    1.095445] pnp 00:06: [io  0x0061]
Feb 14 19:32:42 debian kernel: [    1.095489] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
Feb 14 19:32:42 debian kernel: [    1.095505] pnp 00:07: [io  0x0060]
Feb 14 19:32:42 debian kernel: [    1.095508] pnp 00:07: [io  0x0064]
Feb 14 19:32:42 debian kernel: [    1.095514] pnp 00:07: [irq 1]
Feb 14 19:32:42 debian kernel: [    1.095556] pnp 00:07: Plug and Play ACPI device, IDs TOS1101 PNP0303 (active)
Feb 14 19:32:42 debian kernel: [    1.095575] pnp 00:08: [irq 12]
Feb 14 19:32:42 debian kernel: [    1.095620] pnp 00:08: Plug and Play ACPI device, IDs TOS0330 SYN1900 SYN0002 PNP0f13 (active)
Feb 14 19:32:42 debian kernel: [    1.095634] pnp 00:09: [io  0x0b20-0x0b3f]
Feb 14 19:32:42 debian kernel: [    1.095637] pnp 00:09: IRQ 7 override to edge, high
Feb 14 19:32:42 debian kernel: [    1.095643] pnp 00:09: [irq 7]
Feb 14 19:32:42 debian kernel: [    1.095688] pnp 00:09: Plug and Play ACPI device, IDs SMB0001 (active)
Feb 14 19:32:42 debian kernel: [    1.095704] pnp 00:0a: [io  0x0010-0x001f]
Feb 14 19:32:42 debian kernel: [    1.095707] pnp 00:0a: [io  0x002e-0x002f]
Feb 14 19:32:42 debian kernel: [    1.095709] pnp 00:0a: [io  0x0062]
Feb 14 19:32:42 debian kernel: [    1.095711] pnp 00:0a: [io  0x0066]
Feb 14 19:32:42 debian kernel: [    1.095714] pnp 00:0a: [io  0x0068]
Feb 14 19:32:42 debian kernel: [    1.095716] pnp 00:0a: [io  0x006c]
Feb 14 19:32:42 debian kernel: [    1.095718] pnp 00:0a: [io  0x0072-0x0073]
Feb 14 19:32:42 debian kernel: [    1.095720] pnp 00:0a: [io  0x0080]
Feb 14 19:32:42 debian kernel: [    1.095722] pnp 00:0a: [io  0x00b0-0x00b1]
Feb 14 19:32:42 debian kernel: [    1.095725] pnp 00:0a: [io  0x0092]
Feb 14 19:32:42 debian kernel: [    1.095727] pnp 00:0a: [io  0x0400-0x04cf]
Feb 14 19:32:42 debian kernel: [    1.095729] pnp 00:0a: [io  0x04d0-0x04d1]
Feb 14 19:32:42 debian kernel: [    1.095731] pnp 00:0a: [io  0x04d6]
Feb 14 19:32:42 debian kernel: [    1.095734] pnp 00:0a: [io  0x0680-0x06ff]
Feb 14 19:32:42 debian kernel: [    1.095736] pnp 00:0a: [io  0x077a]
Feb 14 19:32:42 debian kernel: [    1.095738] pnp 00:0a: [io  0x0c00-0x0c01]
Feb 14 19:32:42 debian kernel: [    1.095742] pnp 00:0a: [io  0x0c14]
Feb 14 19:32:42 debian kernel: [    1.095744] pnp 00:0a: [io  0x0c50-0x0c52]
Feb 14 19:32:42 debian kernel: [    1.095747] pnp 00:0a: [io  0x0c6c]
Feb 14 19:32:42 debian kernel: [    1.095749] pnp 00:0a: [io  0x0c6f]
Feb 14 19:32:42 debian kernel: [    1.095751] pnp 00:0a: [io  0x0cd0-0x0cdb]
Feb 14 19:32:42 debian kernel: [    1.095753] pnp 00:0a: [io  0x0840-0x0847]
Feb 14 19:32:42 debian kernel: [    1.095832] system 00:0a: [io  0x0400-0x04cf] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095836] system 00:0a: [io  0x04d0-0x04d1] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095839] system 00:0a: [io  0x04d6] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095842] system 00:0a: [io  0x0680-0x06ff] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095845] system 00:0a: [io  0x077a] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095848] system 00:0a: [io  0x0c00-0x0c01] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095853] system 00:0a: [io  0x0c14] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095857] system 00:0a: [io  0x0c50-0x0c52] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095860] system 00:0a: [io  0x0c6c] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095863] system 00:0a: [io  0x0c6f] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095866] system 00:0a: [io  0x0cd0-0x0cdb] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095869] system 00:0a: [io  0x0840-0x0847] has been reserved
Feb 14 19:32:42 debian kernel: [    1.095873] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 14 19:32:42 debian kernel: [    1.095949] pnp 00:0b: [mem 0xff700000-0xff70ffff]
Feb 14 19:32:42 debian kernel: [    1.095952] pnp 00:0b: [mem 0x000e0000-0x000fffff]
Feb 14 19:32:42 debian kernel: [    1.095955] pnp 00:0b: [mem 0xff800000-0xffffffff]
Feb 14 19:32:42 debian kernel: [    1.096045] system 00:0b: [mem 0xff700000-0xff70ffff] has been reserved
Feb 14 19:32:42 debian kernel: [    1.096049] system 00:0b: [mem 0x000e0000-0x000fffff] could not be reserved
Feb 14 19:32:42 debian kernel: [    1.096053] system 00:0b: [mem 0xff800000-0xffffffff] has been reserved
Feb 14 19:32:42 debian kernel: [    1.096056] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
Feb 14 19:32:42 debian kernel: [    1.097642] pnp: PnP ACPI: found 12 devices
Feb 14 19:32:42 debian kernel: [    1.097645] ACPI: ACPI bus type pnp unregistered
Feb 14 19:32:42 debian kernel: [    1.105667] pci 0000:00:01.0: address space collision: [mem 0xfffe0000-0xffffffff pref] conflicts with reserved [mem 0xff800000-0xffffffff]
Feb 14 19:32:42 debian kernel: [    1.105688] PCI: max bus depth: 1 pci_try_num: 2
Feb 14 19:32:42 debian kernel: [    1.105722] pci 0000:00:01.0: BAR 6: assigned [mem 0xf2c80000-0xf2c9ffff pref]
Feb 14 19:32:42 debian kernel: [    1.105732] pci 0000:00:02.4: BAR 15: assigned [mem 0xf2d00000-0xf2efffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.105738] pci 0000:00:02.4: BAR 13: assigned [io  0x1000-0x1fff]
Feb 14 19:32:42 debian kernel: [    1.105742] pci 0000:00:02.2: PCI bridge to [bus 01-04]
Feb 14 19:32:42 debian kernel: [    1.105746] pci 0000:00:02.2:   bridge window [io  0x2000-0x2fff]
Feb 14 19:32:42 debian kernel: [    1.105751] pci 0000:00:02.2:   bridge window [mem 0xf1000000-0xf1ffffff]
Feb 14 19:32:42 debian kernel: [    1.105755] pci 0000:00:02.2:   bridge window [mem 0xf0000000-0xf0ffffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.105761] pci 0000:00:02.3: PCI bridge to [bus 05-05]
Feb 14 19:32:42 debian kernel: [    1.105766] pci 0000:00:02.3:   bridge window [mem 0xf2b00000-0xf2bfffff]
Feb 14 19:32:42 debian kernel: [    1.105774] pci 0000:00:02.4: PCI bridge to [bus 06-06]
Feb 14 19:32:42 debian kernel: [    1.105777] pci 0000:00:02.4:   bridge window [io  0x1000-0x1fff]
Feb 14 19:32:42 debian kernel: [    1.105782] pci 0000:00:02.4:   bridge window [mem 0xf2a00000-0xf2afffff]
Feb 14 19:32:42 debian kernel: [    1.105786] pci 0000:00:02.4:   bridge window [mem 0xf2d00000-0xf2efffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.105812] pci 0000:00:02.2: setting latency timer to 64
Feb 14 19:32:42 debian kernel: [    1.105831] pci 0000:00:02.3: setting latency timer to 64
Feb 14 19:32:42 debian kernel: [    1.105846] pci 0000:00:02.4: setting latency timer to 64
Feb 14 19:32:42 debian kernel: [    1.105851] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Feb 14 19:32:42 debian kernel: [    1.105854] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Feb 14 19:32:42 debian kernel: [    1.105857] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Feb 14 19:32:42 debian kernel: [    1.105860] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
Feb 14 19:32:42 debian kernel: [    1.105863] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
Feb 14 19:32:42 debian kernel: [    1.105866] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
Feb 14 19:32:42 debian kernel: [    1.105868] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
Feb 14 19:32:42 debian kernel: [    1.105871] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
Feb 14 19:32:42 debian kernel: [    1.105874] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
Feb 14 19:32:42 debian kernel: [    1.105877] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
Feb 14 19:32:42 debian kernel: [    1.105880] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
Feb 14 19:32:42 debian kernel: [    1.105883] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
Feb 14 19:32:42 debian kernel: [    1.105886] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
Feb 14 19:32:42 debian kernel: [    1.105889] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
Feb 14 19:32:42 debian kernel: [    1.105891] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
Feb 14 19:32:42 debian kernel: [    1.105894] pci_bus 0000:00: resource 19 [mem 0xe0000000-0xf7ffffff]
Feb 14 19:32:42 debian kernel: [    1.105897] pci_bus 0000:00: resource 20 [mem 0xfc000000-0xfed3ffff]
Feb 14 19:32:42 debian kernel: [    1.105900] pci_bus 0000:00: resource 21 [mem 0xfed45000-0xffffffff]
Feb 14 19:32:42 debian kernel: [    1.105903] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
Feb 14 19:32:42 debian kernel: [    1.105906] pci_bus 0000:01: resource 1 [mem 0xf1000000-0xf1ffffff]
Feb 14 19:32:42 debian kernel: [    1.105909] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf0ffffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.105913] pci_bus 0000:05: resource 1 [mem 0xf2b00000-0xf2bfffff]
Feb 14 19:32:42 debian kernel: [    1.105916] pci_bus 0000:06: resource 0 [io  0x1000-0x1fff]
Feb 14 19:32:42 debian kernel: [    1.105918] pci_bus 0000:06: resource 1 [mem 0xf2a00000-0xf2afffff]
Feb 14 19:32:42 debian kernel: [    1.105921] pci_bus 0000:06: resource 2 [mem 0xf2d00000-0xf2efffff 64bit pref]
Feb 14 19:32:42 debian kernel: [    1.106065] NET: Registered protocol family 2
Feb 14 19:32:42 debian kernel: [    1.111450] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Feb 14 19:32:42 debian kernel: [    1.113073] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Feb 14 19:32:42 debian kernel: [    1.115651] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Feb 14 19:32:42 debian kernel: [    1.115965] TCP: Hash tables configured (established 524288 bind 65536)
Feb 14 19:32:42 debian kernel: [    1.115969] TCP reno registered
Feb 14 19:32:42 debian kernel: [    1.115992] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Feb 14 19:32:42 debian kernel: [    1.116089] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Feb 14 19:32:42 debian kernel: [    1.116330] NET: Registered protocol family 1
Feb 14 19:32:42 debian kernel: [    1.116353] pci 0000:00:01.0: Boot video device
Feb 14 19:32:42 debian kernel: [    1.116385] ACPI: Cannot set device to a higher-powered state than parent
Feb 14 19:32:42 debian kernel: [    1.116389] ACPI: Cannot set device to a higher-powered state than parent
Feb 14 19:32:42 debian kernel: [    1.125827] PCI: CLS 64 bytes, default 64
Feb 14 19:32:42 debian kernel: [    1.125908] Unpacking initramfs...
Feb 14 19:32:42 debian kernel: [    1.411439] Freeing initrd memory: 11020k freed
Feb 14 19:32:42 debian kernel: [    1.415062] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Feb 14 19:32:42 debian kernel: [    1.415069] Placing 64MB software IO TLB between ffff880091540000 - ffff880095540000
Feb 14 19:32:42 debian kernel: [    1.415072] software IO TLB at phys 0x91540000 - 0x95540000
Feb 14 19:32:42 debian kernel: [    1.415113] Simple Boot Flag at 0x44 set to 0x1
Feb 14 19:32:42 debian kernel: [    1.415624] perf: AMD IBS detected (0x000000ff)
Feb 14 19:32:42 debian kernel: [    1.415941] audit: initializing netlink socket (disabled)
Feb 14 19:32:42 debian kernel: [    1.415957] type=2000 audit(1423938747.408:1): initialized
Feb 14 19:32:42 debian kernel: [    1.432816] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Feb 14 19:32:42 debian kernel: [    1.434258] VFS: Disk quotas dquot_6.5.2
Feb 14 19:32:42 debian kernel: [    1.434304] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Feb 14 19:32:42 debian kernel: [    1.434397] msgmni has been set to 13911
Feb 14 19:32:42 debian kernel: [    1.434636] alg: No test for stdrng (krng)
Feb 14 19:32:42 debian kernel: [    1.434681] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Feb 14 19:32:42 debian kernel: [    1.434685] io scheduler noop registered
Feb 14 19:32:42 debian kernel: [    1.434687] io scheduler deadline registered
Feb 14 19:32:42 debian kernel: [    1.434721] io scheduler cfq registered (default)
Feb 14 19:32:42 debian kernel: [    1.435001] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 14 19:32:42 debian kernel: [    1.435031] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Feb 14 19:32:42 debian kernel: [    1.435033] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Feb 14 19:32:42 debian kernel: [    1.435493] efifb: probing for efifb
Feb 14 19:32:42 debian kernel: [    1.436256] efifb: framebuffer at 0xe0000000, mapped to 0xffffc9000a280000, using 5632k, total 5632k
Feb 14 19:32:42 debian kernel: [    1.436260] efifb: mode is 1600x900x32, linelength=6400, pages=1
Feb 14 19:32:42 debian kernel: [    1.436262] efifb: scrolling: redraw
Feb 14 19:32:42 debian kernel: [    1.436265] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Feb 14 19:32:42 debian kernel: [    1.442893] Console: switching to colour frame buffer device 200x56
Feb 14 19:32:42 debian kernel: [    1.448915] fb0: EFI VGA frame buffer device
Feb 14 19:32:42 debian kernel: [    1.448962] ERST: Table is not found!
Feb 14 19:32:42 debian kernel: [    1.448964] GHES: HEST is not enabled!
Feb 14 19:32:42 debian kernel: [    1.449050] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Feb 14 19:32:42 debian kernel: [    1.616957] Linux agpgart interface v0.103
Feb 14 19:32:42 debian kernel: [    1.617137] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Feb 14 19:32:42 debian kernel: [    1.619709] serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 14 19:32:42 debian kernel: [    1.619720] serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 14 19:32:42 debian kernel: [    1.619922] mousedev: PS/2 mouse device common for all mice
Feb 14 19:32:42 debian kernel: [    1.619982] rtc_cmos 00:05: RTC can wake from S4
Feb 14 19:32:42 debian kernel: [    1.620112] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
Feb 14 19:32:42 debian kernel: [    1.620134] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Feb 14 19:32:42 debian kernel: [    1.620150] cpuidle: using governor ladder
Feb 14 19:32:42 debian kernel: [    1.620152] cpuidle: using governor menu
Feb 14 19:32:42 debian kernel: [    1.620445] TCP cubic registered
Feb 14 19:32:42 debian kernel: [    1.620558] NET: Registered protocol family 10
Feb 14 19:32:42 debian kernel: [    1.621181] Mobile IPv6
Feb 14 19:32:42 debian kernel: [    1.621184] NET: Registered protocol family 17
Feb 14 19:32:42 debian kernel: [    1.621190] Registering the dns_resolver key type
Feb 14 19:32:42 debian kernel: [    1.621390] PM: Hibernation image not present or could not be loaded.
Feb 14 19:32:42 debian kernel: [    1.621407] registered taskstats version 1
Feb 14 19:32:42 debian kernel: [    1.622487] rtc_cmos 00:05: setting system clock to 2015-02-14 18:32:28 UTC (1423938748)
Feb 14 19:32:42 debian kernel: [    1.622598] Initializing network drop monitor service
Feb 14 19:32:42 debian kernel: [    1.624177] Freeing unused kernel memory: 576k freed
Feb 14 19:32:42 debian kernel: [    1.624323] Write protecting the kernel read-only data: 6144k
Feb 14 19:32:42 debian kernel: [    1.627597] Freeing unused kernel memory: 644k freed
Feb 14 19:32:42 debian kernel: [    1.631155] Freeing unused kernel memory: 688k freed
Feb 14 19:32:42 debian kernel: [    1.638545] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
Feb 14 19:32:42 debian kernel: [    1.680094] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Feb 14 19:32:42 debian kernel: [    1.680174] r8169 0000:01:00.0: (unregistered net_device): unknown MAC, using family default
Feb 14 19:32:42 debian kernel: [    1.680183] r8169 0000:01:00.0: setting latency timer to 64
Feb 14 19:32:42 debian kernel: [    1.680235] r8169 0000:01:00.0: irq 72 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    1.680873] r8169 0000:01:00.0: eth0: RTL8101e at 0xffffc90000046000, 00:8c:fa:86:90:5a, XID 04900000 IRQ 72
Feb 14 19:32:42 debian kernel: [    1.687385] usbcore: registered new interface driver usbfs
Feb 14 19:32:42 debian kernel: [    1.687428] usbcore: registered new interface driver hub
Feb 14 19:32:42 debian kernel: [    1.689512] SCSI subsystem initialized
Feb 14 19:32:42 debian kernel: [    1.692306] usbcore: registered new device driver usb
Feb 14 19:32:42 debian kernel: [    1.693201] ACPI: Cannot set device to a higher-powered state than parent
Feb 14 19:32:42 debian kernel: [    1.693207] ACPI: Cannot set device to a higher-powered state than parent
Feb 14 19:32:42 debian kernel: [    1.693253] xhci_hcd 0000:00:10.0: setting latency timer to 64
Feb 14 19:32:42 debian kernel: [    1.693258] xhci_hcd 0000:00:10.0: xHCI Host Controller
Feb 14 19:32:42 debian kernel: [    1.693301] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb 14 19:32:42 debian kernel: [    1.693557] xhci_hcd 0000:00:10.0: irq 73 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    1.693565] xhci_hcd 0000:00:10.0: irq 74 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    1.693573] xhci_hcd 0000:00:10.0: irq 75 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    1.693583] xhci_hcd 0000:00:10.0: irq 76 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    1.693590] xhci_hcd 0000:00:10.0: irq 77 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    1.693710] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Feb 14 19:32:42 debian kernel: [    1.693714] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 19:32:42 debian kernel: [    1.693717] usb usb1: Product: xHCI Host Controller
Feb 14 19:32:42 debian kernel: [    1.693720] usb usb1: Manufacturer: Linux 3.2.0-4-amd64 xhci_hcd
Feb 14 19:32:42 debian kernel: [    1.693722] usb usb1: SerialNumber: 0000:00:10.0
Feb 14 19:32:42 debian kernel: [    1.695293] xHCI xhci_add_endpoint called for root hub
Feb 14 19:32:42 debian kernel: [    1.695298] xHCI xhci_check_bandwidth called for root hub
Feb 14 19:32:42 debian kernel: [    1.695350] hub 1-0:1.0: USB hub found
Feb 14 19:32:42 debian kernel: [    1.695361] hub 1-0:1.0: 2 ports detected
Feb 14 19:32:42 debian kernel: [    1.695631] xhci_hcd 0000:00:10.0: xHCI Host Controller
Feb 14 19:32:42 debian kernel: [    1.695643] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
Feb 14 19:32:42 debian kernel: [    1.696921] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
Feb 14 19:32:42 debian kernel: [    1.696925] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 19:32:42 debian kernel: [    1.696929] usb usb2: Product: xHCI Host Controller
Feb 14 19:32:42 debian kernel: [    1.696932] usb usb2: Manufacturer: Linux 3.2.0-4-amd64 xhci_hcd
Feb 14 19:32:42 debian kernel: [    1.696934] usb usb2: SerialNumber: 0000:00:10.0
Feb 14 19:32:42 debian kernel: [    1.697299] thermal LNXTHERM:00: registered as thermal_zone0
Feb 14 19:32:42 debian kernel: [    1.697303] ACPI: Thermal Zone [THZN] (53 C)
Feb 14 19:32:42 debian kernel: [    1.697733] xHCI xhci_add_endpoint called for root hub
Feb 14 19:32:42 debian kernel: [    1.697737] xHCI xhci_check_bandwidth called for root hub
Feb 14 19:32:42 debian kernel: [    1.697786] hub 2-0:1.0: USB hub found
Feb 14 19:32:42 debian kernel: [    1.697797] hub 2-0:1.0: 2 ports detected
Feb 14 19:32:42 debian kernel: [    1.697955] ACPI: Fan [FAN1] (off)
Feb 14 19:32:42 debian kernel: [    1.700169] libata version 3.00 loaded.
Feb 14 19:32:42 debian kernel: [    1.708771] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Feb 14 19:32:42 debian kernel: [    1.712123] ahci 0000:00:11.0: version 3.0
Feb 14 19:32:42 debian kernel: [    1.712249] ahci 0000:00:11.0: irq 78 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    1.712319] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
Feb 14 19:32:42 debian kernel: [    1.712325] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp fbs pio slum part 
Feb 14 19:32:42 debian kernel: [    1.714661] scsi0 : ahci
Feb 14 19:32:42 debian kernel: [    1.716278] scsi1 : ahci
Feb 14 19:32:42 debian kernel: [    1.851350] ata1: SATA max UDMA/133 abar m1024@0xf2c6e000 port 0xf2c6e100 irq 78
Feb 14 19:32:42 debian kernel: [    1.851356] ata2: SATA max UDMA/133 abar m1024@0xf2c6e000 port 0xf2c6e180 irq 78
Feb 14 19:32:42 debian kernel: [    1.851429] ehci_hcd 0000:00:12.0: EHCI Host Controller
Feb 14 19:32:42 debian kernel: [    1.851460] ehci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
Feb 14 19:32:42 debian kernel: [    1.851473] ehci_hcd 0000:00:12.0: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Feb 14 19:32:42 debian kernel: [    1.851498] ehci_hcd 0000:00:12.0: debug port 2
Feb 14 19:32:42 debian kernel: [    1.851528] ehci_hcd 0000:00:12.0: irq 18, io mem 0xf2c6d000
Feb 14 19:32:42 debian kernel: [    1.860193] ehci_hcd 0000:00:12.0: USB 2.0 started, EHCI 1.00
Feb 14 19:32:42 debian kernel: [    1.860246] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Feb 14 19:32:42 debian kernel: [    1.860249] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 19:32:42 debian kernel: [    1.860252] usb usb3: Product: EHCI Host Controller
Feb 14 19:32:42 debian kernel: [    1.860254] usb usb3: Manufacturer: Linux 3.2.0-4-amd64 ehci_hcd
Feb 14 19:32:42 debian kernel: [    1.860257] usb usb3: SerialNumber: 0000:00:12.0
Feb 14 19:32:42 debian kernel: [    1.860496] hub 3-0:1.0: USB hub found
Feb 14 19:32:42 debian kernel: [    1.860502] hub 3-0:1.0: 2 ports detected
Feb 14 19:32:42 debian kernel: [    1.860649] ehci_hcd 0000:00:13.0: EHCI Host Controller
Feb 14 19:32:42 debian kernel: [    1.860661] ehci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
Feb 14 19:32:42 debian kernel: [    1.860670] ehci_hcd 0000:00:13.0: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Feb 14 19:32:42 debian kernel: [    1.860691] ehci_hcd 0000:00:13.0: debug port 2
Feb 14 19:32:42 debian kernel: [    1.860707] ehci_hcd 0000:00:13.0: irq 18, io mem 0xf2c6c000
Feb 14 19:32:42 debian kernel: [    1.872060] ehci_hcd 0000:00:13.0: USB 2.0 started, EHCI 1.00
Feb 14 19:32:42 debian kernel: [    1.872117] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
Feb 14 19:32:42 debian kernel: [    1.872120] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Feb 14 19:32:42 debian kernel: [    1.872123] usb usb4: Product: EHCI Host Controller
Feb 14 19:32:42 debian kernel: [    1.872126] usb usb4: Manufacturer: Linux 3.2.0-4-amd64 ehci_hcd
Feb 14 19:32:42 debian kernel: [    1.872128] usb usb4: SerialNumber: 0000:00:13.0
Feb 14 19:32:42 debian kernel: [    1.872354] hub 4-0:1.0: USB hub found
Feb 14 19:32:42 debian kernel: [    1.872361] hub 4-0:1.0: 2 ports detected
Feb 14 19:32:42 debian kernel: [    2.172211] usb 3-1: new high-speed USB device number 2 using ehci_hcd
Feb 14 19:32:42 debian kernel: [    2.305248] usb 3-1: New USB device found, idVendor=0438, idProduct=7900
Feb 14 19:32:42 debian kernel: [    2.305253] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Feb 14 19:32:42 debian kernel: [    2.305546] hub 3-1:1.0: USB hub found
Feb 14 19:32:42 debian kernel: [    2.305615] hub 3-1:1.0: 4 ports detected
Feb 14 19:32:42 debian kernel: [    2.340201] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Feb 14 19:32:42 debian kernel: [    2.340227] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Feb 14 19:32:42 debian kernel: [    2.343621] ata2.00: ATAPI: TSSTcorp CDDVDW SU-208FB, TF01, max UDMA/100
Feb 14 19:32:42 debian kernel: [    2.346261] ata2.00: configured for UDMA/100
Feb 14 19:32:42 debian kernel: [    2.375107] ata1.00: ATA-8: TOSHIBA MQ01ABD100, AX1P4M, max UDMA/100
Feb 14 19:32:42 debian kernel: [    2.375113] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Feb 14 19:32:42 debian kernel: [    2.377000] ata1.00: configured for UDMA/100
Feb 14 19:32:42 debian kernel: [    2.377277] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MQ01ABD1 AX1P PQ: 0 ANSI: 5
Feb 14 19:32:42 debian kernel: [    2.380151] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW SU-208FB  TF01 PQ: 0 ANSI: 5
Feb 14 19:32:42 debian kernel: [    2.385442] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Feb 14 19:32:42 debian kernel: [    2.385583] sd 0:0:0:0: [sda] Write Protect is off
Feb 14 19:32:42 debian kernel: [    2.385587] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 14 19:32:42 debian kernel: [    2.385640] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 14 19:32:42 debian kernel: [    2.393988] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Feb 14 19:32:42 debian kernel: [    2.393994] cdrom: Uniform CD-ROM driver Revision: 3.20
Feb 14 19:32:42 debian kernel: [    2.394236] sr 1:0:0:0: Attached scsi CD-ROM sr0
Feb 14 19:32:42 debian kernel: [    2.412200] Refined TSC clocksource calibration: 1996.256 MHz.
Feb 14 19:32:42 debian kernel: [    2.412213] Switching to clocksource tsc
Feb 14 19:32:42 debian kernel: [    2.416217] usb 4-1: new high-speed USB device number 2 using ehci_hcd
Feb 14 19:32:42 debian kernel: [    2.505143]  sda: sda1 sda2 sda3 sda4
Feb 14 19:32:42 debian kernel: [    2.505810] sd 0:0:0:0: [sda] Attached SCSI disk
Feb 14 19:32:42 debian kernel: [    2.508490] sd 0:0:0:0: Attached scsi generic sg0 type 0
Feb 14 19:32:42 debian kernel: [    2.508561] sr 1:0:0:0: Attached scsi generic sg1 type 5
Feb 14 19:32:42 debian kernel: [    2.552531] usb 4-1: New USB device found, idVendor=0438, idProduct=7900
Feb 14 19:32:42 debian kernel: [    2.552536] usb 4-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Feb 14 19:32:42 debian kernel: [    2.552813] hub 4-1:1.0: USB hub found
Feb 14 19:32:42 debian kernel: [    2.552888] hub 4-1:1.0: 4 ports detected
Feb 14 19:32:42 debian kernel: [    2.840254] usb 4-1.1: new full-speed USB device number 3 using ehci_hcd
Feb 14 19:32:42 debian kernel: [    2.950964] usb 4-1.1: New USB device found, idVendor=0930, idProduct=0225
Feb 14 19:32:42 debian kernel: [    2.950971] usb 4-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Feb 14 19:32:42 debian kernel: [    2.950975] usb 4-1.1: Product: BCM43142A0
Feb 14 19:32:42 debian kernel: [    2.950977] usb 4-1.1: Manufacturer: Broadcom Corp
Feb 14 19:32:42 debian kernel: [    2.950980] usb 4-1.1: SerialNumber: 645A04D4D14B
Feb 14 19:32:42 debian kernel: [    3.025007] usb 4-1.2: new high-speed USB device number 4 using ehci_hcd
Feb 14 19:32:42 debian kernel: [    3.192464] PM: Starting manual resume from disk
Feb 14 19:32:42 debian kernel: [    3.192468] PM: Hibernation image partition 8:3 present
Feb 14 19:32:42 debian kernel: [    3.192471] PM: Looking for hibernation image.
Feb 14 19:32:42 debian kernel: [    3.211584] PM: Image not found (code -22)
Feb 14 19:32:42 debian kernel: [    3.211588] PM: Hibernation image not present or could not be loaded.
Feb 14 19:32:42 debian kernel: [    3.214567] usb 4-1.2: New USB device found, idVendor=10f1, idProduct=1a5b
Feb 14 19:32:42 debian kernel: [    3.214571] usb 4-1.2: New USB device strings: Mfr=2, Product=1, SerialNumber=0
Feb 14 19:32:42 debian kernel: [    3.214574] usb 4-1.2: Product: TOSHIBA Web Camera - HD
Feb 14 19:32:42 debian kernel: [    3.214577] usb 4-1.2: Manufacturer: Sonix Technology Co., Ltd.
Feb 14 19:32:42 debian kernel: [    3.596583] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Feb 14 19:32:42 debian kernel: [    6.075759] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
Feb 14 19:32:42 debian kernel: [    6.075768] ACPI: Power Button [PWRB]
Feb 14 19:32:42 debian kernel: [    6.075850] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
Feb 14 19:32:42 debian kernel: [    6.076241] ACPI: Lid Switch [LID0]
Feb 14 19:32:42 debian kernel: [    6.076318] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Feb 14 19:32:42 debian kernel: [    6.076323] ACPI: Power Button [PWRF]
Feb 14 19:32:42 debian kernel: [    6.132399] ACPI: acpi_idle registered with cpuidle
Feb 14 19:32:42 debian kernel: [    6.132868] acpi device:00: registered as cooling_device3
Feb 14 19:32:42 debian kernel: [    6.132955] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
Feb 14 19:32:42 debian kernel: [    6.132963] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Feb 14 19:32:42 debian kernel: [    6.135322] EFI Variables Facility v0.08 2004-May-17
Feb 14 19:32:42 debian kernel: [    6.333906] toshiba_bluetooth: Detected Toshiba ACPI Bluetooth device - installing RFKill handler
Feb 14 19:32:42 debian kernel: [    6.338454] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMB0 [io 0xb00-0xb0f]
Feb 14 19:32:42 debian kernel: [    6.338458] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Feb 14 19:32:42 debian kernel: [    6.384276] toshiba_bluetooth: Re-enabling Toshiba Bluetooth
Feb 14 19:32:42 debian kernel: [    6.403454] wmi: Mapper loaded
Feb 14 19:32:42 debian kernel: [    6.476068] input: PC Speaker as /devices/platform/pcspkr/input/input5
Feb 14 19:32:42 debian kernel: [    6.510995] ACPI: AC Adapter [ADP0] (on-line)
Feb 14 19:32:42 debian kernel: [    6.574546] alg: No test for __gcm-aes-aesni (__driver-gcm-aes-aesni)
Feb 14 19:32:42 debian kernel: [    6.788216] ACPI: Battery Slot [BAT0] (battery present)
Feb 14 19:32:42 debian kernel: [    6.894634] snd_hda_intel 0000:00:01.1: irq 79 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    6.894665] snd_hda_intel 0000:00:01.1: setting latency timer to 64
Feb 14 19:32:42 debian kernel: [    6.910591] cfg80211: Calling CRDA to update world regulatory domain
Feb 14 19:32:42 debian kernel: [    7.079499] powernow-k8: Found 1 AMD A8-6410 APU with AMD Radeon R5 Graphics     (4 cpu cores) (version 2.20.00)
Feb 14 19:32:42 debian kernel: [    7.079513] powernow-k8: Core Performance Boosting: on.
Feb 14 19:32:42 debian kernel: [    7.079611] powernow-k8:    0 : pstate 0 (2000 MHz)
Feb 14 19:32:42 debian kernel: [    7.079614] powernow-k8:    1 : pstate 1 (1800 MHz)
Feb 14 19:32:42 debian kernel: [    7.079616] powernow-k8:    2 : pstate 2 (1600 MHz)
Feb 14 19:32:42 debian kernel: [    7.079619] powernow-k8:    3 : pstate 3 (1400 MHz)
Feb 14 19:32:42 debian kernel: [    7.079621] powernow-k8:    4 : pstate 4 (1200 MHz)
Feb 14 19:32:42 debian kernel: [    7.079623] powernow-k8:    5 : pstate 5 (1000 MHz)
Feb 14 19:32:42 debian kernel: [    7.098600] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19
Feb 14 19:32:42 debian kernel: [    7.098974] input: Toshiba input device as /devices/virtual/input/input6
Feb 14 19:32:42 debian kernel: [    7.180194] Registered led device: toshiba::illumination
Feb 14 19:32:42 debian kernel: [    7.229288] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
Feb 14 19:32:42 debian kernel: [    7.263094] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
Feb 14 19:32:42 debian kernel: [    7.532242] wl: module license 'unspecified' taints kernel.
Feb 14 19:32:42 debian kernel: [    7.532252] Disabling lock debugging due to kernel taint
Feb 14 19:32:42 debian kernel: [    7.573244] HDMI status: Codec=0 Pin=3 Presence_Detect=0 ELD_Valid=0
Feb 14 19:32:42 debian kernel: [    7.573514] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input8
Feb 14 19:32:42 debian kernel: [    7.573872] wl 0000:05:00.0: setting latency timer to 64
Feb 14 19:32:42 debian kernel: [    7.575747] snd_hda_intel 0000:00:14.2: irq 80 for MSI/MSI-X
Feb 14 19:32:42 debian kernel: [    7.616693] eth1: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
Feb 14 19:32:42 debian kernel: [    7.700034] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input9
Feb 14 19:32:42 debian kernel: [    7.704043] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input10
Feb 14 19:32:42 debian kernel: [    7.704279] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input11
Feb 14 19:32:42 debian kernel: [    8.261261] cfg80211: World regulatory domain updated:
Feb 14 19:32:42 debian kernel: [    8.261271] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 14 19:32:42 debian kernel: [    8.261279] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:42 debian kernel: [    8.261286] cfg80211:     (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:42 debian kernel: [    8.261293] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:42 debian kernel: [    8.261299] cfg80211:     (5170000 KHz - 5250000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:42 debian kernel: [    8.261305] cfg80211:     (5250000 KHz - 5330000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:42 debian kernel: [    8.261311] cfg80211:     (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:42 debian kernel: [    8.261317] cfg80211:     (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:42 debian kernel: [    8.261323] cfg80211:     (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm)
Feb 14 19:32:42 debian kernel: [    8.721922] Linux media interface: v0.10
Feb 14 19:32:42 debian kernel: [    8.792547] Linux video capture interface: v2.00
Feb 14 19:32:42 debian kernel: [    9.060888] uvcvideo: Found UVC 1.00 device TOSHIBA Web Camera - HD (10f1:1a5b)
Feb 14 19:32:42 debian kernel: [    9.094786] input: TOSHIBA Web Camera - HD as /devices/pci0000:00/0000:00:13.0/usb4/4-1/4-1.2/4-1.2:1.0/input/input12
Feb 14 19:32:42 debian kernel: [    9.095038] usbcore: registered new interface driver uvcvideo
Feb 14 19:32:42 debian kernel: [    9.095044] USB Video Class driver (1.1.1)
Feb 14 19:32:42 debian kernel: [   11.237942] Adding 7300092k swap on /dev/sda3.  Priority:-1 extents:1 across:7300092k 
Feb 14 19:32:42 debian kernel: [   11.273286] EXT4-fs (sda2): re-mounted. Opts: (null)
Feb 14 19:32:42 debian kernel: [   11.503527] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
Feb 14 19:32:42 debian kernel: [   11.631522] loop: module loaded
Feb 14 19:32:42 debian kernel: [   12.568609] FAT-fs (sda1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
Feb 14 19:32:42 debian kernel: [   13.039255] ip_tables: (C) 2000-2006 Netfilter Core Team
Feb 14 19:32:42 debian kernel: [   13.130193] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Feb 14 19:32:42 debian kernel: [   14.234395] RPC: Registered named UNIX socket transport module.
Feb 14 19:32:42 debian kernel: [   14.234404] RPC: Registered udp transport module.
Feb 14 19:32:42 debian kernel: [   14.234408] RPC: Registered tcp transport module.
Feb 14 19:32:42 debian kernel: [   14.234413] RPC: Registered tcp NFSv4.1 backchannel transport module.
Feb 14 19:32:42 debian kernel: [   14.275817] FS-Cache: Loaded
Feb 14 19:32:42 debian kernel: [   14.333338] FS-Cache: Netfs 'nfs' registered for caching
Feb 14 19:32:42 debian kernel: [   14.349449] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
Feb 14 19:32:43 debian kernel: [   16.919001] input: ACPI Virtual Keyboard Device as /devices/virtual/input/input13
Feb 14 19:32:45 debian kernel: [   19.241464] Bluetooth: Core ver 2.16
Feb 14 19:32:45 debian kernel: [   19.241529] NET: Registered protocol family 31
Feb 14 19:32:45 debian kernel: [   19.241535] Bluetooth: HCI device and connection manager initialized
Feb 14 19:32:45 debian kernel: [   19.241543] Bluetooth: HCI socket layer initialized
Feb 14 19:32:45 debian kernel: [   19.241548] Bluetooth: L2CAP socket layer initialized
Feb 14 19:32:45 debian kernel: [   19.241562] Bluetooth: SCO socket layer initialized
Feb 14 19:32:46 debian kernel: [   19.468034] Bluetooth: RFCOMM TTY layer initialized
Feb 14 19:32:46 debian kernel: [   19.468072] Bluetooth: RFCOMM socket layer initialized
Feb 14 19:32:46 debian kernel: [   19.468077] Bluetooth: RFCOMM ver 1.11
Feb 14 19:32:46 debian kernel: [   19.733660] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Feb 14 19:32:46 debian kernel: [   19.733669] Bluetooth: BNEP filters: protocol multicast
Feb 14 19:32:47 debian kernel: [   20.723018] lp: driver loaded but no devices found
Feb 14 19:32:47 debian kernel: [   20.755738] ppdev: user-space parallel port driver
Feb 14 19:32:48 debian kernel: [   21.401125] r8169 0000:01:00.0: eth0: link down
Feb 14 19:32:48 debian kernel: [   21.404430] ADDRCONF(NETDEV_UP): eth0: link is not ready
Feb 14 19:32:50 debian kernel: [   23.988871] cfg80211: Calling CRDA to update world regulatory domain
Feb 14 19:32:50 debian kernel: [   24.001104] cfg80211: World regulatory domain updated:
Feb 14 19:32:50 debian kernel: [   24.001112] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 14 19:32:50 debian kernel: [   24.001120] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:50 debian kernel: [   24.001127] cfg80211:     (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:50 debian kernel: [   24.001134] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:50 debian kernel: [   24.001140] cfg80211:     (5170000 KHz - 5250000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:50 debian kernel: [   24.001146] cfg80211:     (5250000 KHz - 5330000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:50 debian kernel: [   24.001153] cfg80211:     (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:50 debian kernel: [   24.001159] cfg80211:     (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:50 debian kernel: [   24.001165] cfg80211:     (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm)
Feb 14 19:32:51 debian kernel: [   25.148565] cfg80211: Calling CRDA to update world regulatory domain
Feb 14 19:32:51 debian kernel: [   25.160905] cfg80211: World regulatory domain updated:
Feb 14 19:32:51 debian kernel: [   25.160916] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 14 19:32:51 debian kernel: [   25.160924] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:51 debian kernel: [   25.160931] cfg80211:     (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:51 debian kernel: [   25.160938] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:51 debian kernel: [   25.160945] cfg80211:     (5170000 KHz - 5250000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:51 debian kernel: [   25.160951] cfg80211:     (5250000 KHz - 5330000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:51 debian kernel: [   25.160957] cfg80211:     (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:51 debian kernel: [   25.160964] cfg80211:     (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm)
Feb 14 19:32:51 debian kernel: [   25.160970] cfg80211:     (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm)
Feb 14 19:33:01 debian kernel: [   35.120080] eth1: no IPv6 routers present
Feb 14 19:33:04 debian kernel: [   37.638685] cfg80211: Calling CRDA to update world regulatory domain
Feb 14 19:33:04 debian kernel: [   37.650105] cfg80211: World regulatory domain updated:
Feb 14 19:33:04 debian kernel: [   37.650115] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 14 19:33:04 debian kernel: [   37.650123] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:04 debian kernel: [   37.650130] cfg80211:     (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:04 debian kernel: [   37.650137] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:04 debian kernel: [   37.650144] cfg80211:     (5170000 KHz - 5250000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:04 debian kernel: [   37.650151] cfg80211:     (5250000 KHz - 5330000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:04 debian kernel: [   37.650157] cfg80211:     (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:04 debian kernel: [   37.650163] cfg80211:     (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:04 debian kernel: [   37.650170] cfg80211:     (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm)
Feb 14 19:33:06 debian kernel: [   39.379831] cfg80211: Calling CRDA to update world regulatory domain
Feb 14 19:33:06 debian kernel: [   39.391700] cfg80211: World regulatory domain updated:
Feb 14 19:33:06 debian kernel: [   39.391710] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb 14 19:33:06 debian kernel: [   39.391719] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:06 debian kernel: [   39.391726] cfg80211:     (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:06 debian kernel: [   39.391733] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:06 debian kernel: [   39.391739] cfg80211:     (5170000 KHz - 5250000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:06 debian kernel: [   39.391745] cfg80211:     (5250000 KHz - 5330000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:06 debian kernel: [   39.391752] cfg80211:     (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:06 debian kernel: [   39.391758] cfg80211:     (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm)
Feb 14 19:33:06 debian kernel: [   39.391764] cfg80211:     (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm)
```

Thank you very much for your patience of reader,
Ciao.

---

### Post by Freiklite on 2015-03-06
Hi,
Without answer to my post can you say me against one that package I must launch a report-bug?
Thank you.
Bye.

---

