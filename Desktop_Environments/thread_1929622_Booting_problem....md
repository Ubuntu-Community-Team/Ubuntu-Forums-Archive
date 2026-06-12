---
title: "Booting problem..."
date: 2012-02-22
forum: Desktop Environments
---

### Post by zeljkojagust on 2012-02-22
Hi all! I have Ubuntu 11.10 installation on software raid (two 250 GB disks), Mint Mate Shell and 3.0.0.16 kernel. My problem is that suddenly out of nothing my Ubuntu will not boot no more. It shows grub menu and after that my computer restarts. I have booted with Knoppix Live CD and started my SW Raid (mdadm-startall) with no errors, have tested HDD's (smartctl --test=long), memtest also show no error. I have tried to install grub again, update initramfs, I have added minimal init=/bin/bash to grub boot parameter and always the same thing happens, that is the computer restarts after grub menu shows. Also I have a third disk with Windows 7 (yes I know, blasphemy  right) which works without any problem. Please help, I'm not smart any more.

---

### Post by roelforg on 2012-02-22
Does the CAPS-LOCK light blink before it reboots?
Also, try rebooting with acpi=off

---

