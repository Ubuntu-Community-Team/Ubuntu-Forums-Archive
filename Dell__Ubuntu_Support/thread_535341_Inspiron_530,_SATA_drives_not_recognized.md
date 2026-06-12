---
title: "Inspiron 530, SATA drives not recognized"
date: 2007-08-26
forum: Dell  Ubuntu Support
---

### Post by Walter Dnes on 2007-08-26
This is getting very annoying.  I'm actually a Gentoo user, but since Dell supports Ubuntu, I was hoping to get Ubuntu installed.  No luck.  The pre-loaded Windows Vista works, so the hardware is functional.

I ran into 2 problems...

1) The keyboard types characters twice.  This is for real, not just an echo.  I solved it in Gentoo by booting with the command...
gentoo noapic irqpoll acpi=force
and the keyboard functions properly now.

2) In Gentoo and Knoppix and Xubuntu and Ubuntu the install program can't find the DVD/CD drives (or the hard drives)  after the BIOS portion of the boot.  So the install dies at that point.  Any ideas anyone?

---

