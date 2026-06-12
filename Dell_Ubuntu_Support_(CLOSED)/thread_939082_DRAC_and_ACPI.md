---
title: "DRAC and ACPI"
date: 2008-10-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rowan-jetboy on 2008-10-05
Running Hardy Heron Server on a Dell PowerEdge 1850 with a DRAC 4/I remote access card ...

The DRAC provides remote power cycling, and will power down the OS if it is ACPI aware. Ubuntu Server doesn't come with ACPI, but adding the acpid package works. The power button on the front of the server now powers down Ubuntu before cutting the power.

The problem is that the DRAC card still doesn't recognise Ubuntu as an ACPI aware OS, so the option to 'shutdown operating system first' in the DRAC GUI is still greyed out.

Does anyone know how to get the DRAC to recognise Ubuntu as ACPI aware?

---

