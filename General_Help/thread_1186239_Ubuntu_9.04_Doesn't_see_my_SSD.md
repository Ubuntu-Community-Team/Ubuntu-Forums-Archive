---
title: "Ubuntu 9.04 Doesn't see my SSD"
date: 2009-06-13
forum: General Help
---

### Post by jorgen.boberg on 2009-06-13
Hello,
        I recently purchased a 32Gb Intel E-series SSD (actually Kingston). However my Ubuntu 9.04 (64Bit) doesn't see the disk. The disk is visible in bios and I can install FreeBSD on the drive. Here is some info:

MSI K9NGM2-FID

lspci

```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Quadro NVS 210S/GeForce 6150LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
04:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```fdisk -l

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x656759f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
240 heads, 63 sectors/track, 38761 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38761   293033128+  83  Linux


```dmesg

```

[    5.570349] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[    5.570418] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.

```Any ideas on how to sort this out? I really want to move my install to the new faster disk.

// jpb

---

### Post by Ruhani04 on 2009-06-13
I just bought an OCZ 30GB Vertex SSD and installed 9.04 on it without any problems. However, I did a new install and followed the following tweaks from the OCZ forum:
[http://www.ocztechnologyforum.com/forum/showthread.php?t=54379&highlight=linux](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379&highlight=linux)

I saw that you have Nvidia which might be a problem as I have heard.
You may also want to check your bios settings whether you have IDE or ACHI for the hdd and see if that makes a difference. 
I don't think it has anything to do with Ubuntu but with your mobo not recognizing the ssd.
You probably have to look around in SSD forums and see what the problem could be.
You could start by booting via Live CD and if you don't see the drive as a mass storage device then it is defintely your system. By the way the drives normally always come unformatted that's way it would just show up as a mass storage device.
Good luck

---

### Post by jorgen.boberg on 2009-06-13
Thanks for the tips, I will read the thread, however if you reread my post I say that the mobo sees the disk; Ubuntu doesn't. I have tried with Windows and FreeBSD and they both see the disk fine.

---

### Post by jorgen.boberg on 2009-06-13
Oh yeah. I don't have and IDE vs AHCI setting in my bios and the Intel drive apparently only works in AHCI mode. Maybe that is causing some problem. However I don't see how FreeBSD and Windows could work witht he drive then, unless they have some workaround for this.

---

### Post by Ruhani04 on 2009-06-13
Strange. I am out of ideas as I can't think of the reason why 9.04 can't see the drive.
I have mine on AHCI which works fine. But it shouldn't really make a difference for Ubuntu since your mobo recognizes the drive. Are you using XP ? If this is the case than you definitely have IDE mode as AHCI is not natively supported by XP.
But as I said the drive should work in Ubuntu with IDE or AHCI.

---

