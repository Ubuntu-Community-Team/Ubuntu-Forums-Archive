---
title: "Insprion M5030 booting to black screen."
date: 2011-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dvreno on 2011-02-18
Hello all, I recently purchased a M5030. I can't get Ubuntu to boot with out going into grub and changing splash to acpi=off. If I don't do that it goes to a black screen I have downloaded the FGLRX driver from ATI, Reboot and same issue to no avail, Cant play any games or anything commanding of video proccess power assuming thats because of acpi=off


It seemes like alot of people have this issue, anywork arounds?

---

### Post by Fish3r on 2011-02-20
Hey, have you made the acpi=off change permanent in grub or are you just entering it manually into the command line in grub?

---

### Post by AndyCinDallas on 2011-03-24
**acpi=off** is just the start - in other words, it disables ALL of acpi in order to get you up and running.

What you should do then is to go through a short troubleshooting process so you can pinpoint the exact part of ACPI that needs to be disabled in order to boot (as opposed to all of it) - described here:

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

> If "acpi=off" allows the system to boot, try to isolate the ACPI issue with the following boot parameters

Edit: Try **pci=noacpi** as a boot-parameter - that worked for my Inspiron 5030 and is safer than acpi=off

---

