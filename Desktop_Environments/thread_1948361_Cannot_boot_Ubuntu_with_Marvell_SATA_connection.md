---
title: "Cannot boot Ubuntu with Marvell SATA connection"
date: 2012-03-28
forum: Desktop Environments
---

### Post by ptoye on 2012-03-28
I have an Asus mobo with both Marvell (6Gb/s) and Intel SATA connectors. And the disk drive has dual-boot windows/Ubuntu on it.

With my drive on the Intel connector everything works fine. But when on the Marvell connector, it isn't recognised. This is a general problem - even when booting Linux (I've tried 3 different versions) the drive simply doesn't appear. But a Windows boot works fine.

Once I put the dual-boot system up on the drive (using the Intel connection) I replugged it. On the Marvell connection Grub and Windows boot fine. But if the connection is set to IDE mode, doing a Ubuntu boot produces a totally garbled screen and there doesn't seem to be any way out of it short of holding down the power-off button. If the connection is set to ACHI mode, I get the Ubuntu login screen, but the desktop doesn't appear.

Anyone here got any idea what's going on and how I can get Linux to recognise the drive when plugged into the Marvell socket?

---

### Post by ptoye on 2012-04-03
Tried it again today with the disk in ACHI mode and both Windows and Ubuntu booted in without problems. Odd. But at least it's working!

---

### Post by ptoye on 2012-04-25
Just marking the thread as solved - even if I don't know how it worked!

---

