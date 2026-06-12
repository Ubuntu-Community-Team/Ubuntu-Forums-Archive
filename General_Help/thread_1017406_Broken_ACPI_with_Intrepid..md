---
title: "Broken ACPI with Intrepid."
date: 2008-12-21
forum: General Help
---

### Post by digger95 on 2008-12-21
This appears to be a kernel issue.

ACPI is disabled on boot and as a result I've lost fan control and my processor is overheating.  This was not an issue with Hardy.  When I look at my boot messages I am seeing:

```
dmesg | grep -i acpi
```

```
ACPI Error (tbxfroot-0218): A valid RSDP was not found [20080609]
ACPI: Core revision 20080609
ACPI Exception (tbxface-0627): AE_NO_ACPI_TABLES, While loading namespace from ACPI tables [20080609]
ACPI: Unable to load the System Description Tables
ACPI: Interpreter disabled.

```

I doubt it's a hardware issue since my ACPI worked with older kernels.  As far as I know this was introduced with the 2.6.27.x series kernels.  Turning ACPI off is not an option, so if no resolution I can always revert back to Hardy.

Any thoughts would be appreciated.

Dig

---

