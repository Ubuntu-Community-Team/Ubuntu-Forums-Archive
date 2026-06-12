---
title: "VMWare Tools &amp; /proc/pci"
date: 2004-10-18
forum: General Help
---

### Post by spiraloid on 2004-10-18
Just checking out Ubuntu in VMWare before deciding what to do next, but I'm having a bit of a problem. VMWare Tools depends on /proc/pci being there, and it is not.

On startup there is an error:

PCI: Cannot allocate resource region 4 of device 0000:00:07.1

This appears just before the "Starting ubuntu..." line.

Indeed /proc/pci does not exist, however lspci works just fine. Here is the output from lspci:

```
0000&#58;00&#58;00.0 Host bridge&#58; Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge &#40;rev 01&#41;
0000&#58;00&#58;01.0 PCI bridge&#58; Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge &#40;rev 01&#41;
0000&#58;00&#58;07.0 ISA bridge&#58; Intel Corp. 82371AB/EB/MB PIIX4 ISA &#40;rev 08&#41;
0000&#58;00&#58;07.1 IDE interface&#58; Intel Corp. 82371AB/EB/MB PIIX4 IDE &#40;rev 01&#41;
0000&#58;00&#58;07.3 Bridge&#58; Intel Corp. 82371AB/EB/MB PIIX4 ACPI &#40;rev 08&#41;
0000&#58;00&#58;0f.0 VGA compatible controller&#58; VMWare Inc &#91;VMWare SVGA II&#93; PCI Display Adapter
0000&#58;00&#58;10.0 SCSI storage controller&#58; BusLogic BT-946C &#40;BA80C30&#41; &#91;MultiMaster 10&#93; &#40;rev 01&#41;
0000&#58;00&#58;11.0 Ethernet controller&#58; Advance Micro Devices &#91;AMD&#93; 79c970 &#91;PCnet32 LANCE&#93; &#40;rev 10&#41;
```

The referenced device is the IDE interface. Does this matter at all? What might be causing /proc/pci to not be there?

Thanks :)

Mike

---

