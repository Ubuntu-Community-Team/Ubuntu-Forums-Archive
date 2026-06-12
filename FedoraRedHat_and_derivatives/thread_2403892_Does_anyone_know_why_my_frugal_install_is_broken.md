---
title: "Does anyone know why my frugal install is broken?"
date: 2018-10-17
forum: Fedora/RedHat and derivatives
---

### Post by mrgnome on 2018-10-17
Owing to a large number of different reasons, I find myself having to reinstall Windows 10, using my installation of Fedora (KDE spin). Since the only larger-than-4GB USB I have returns a "corrupted files" error (0x80070570), I'm trying to install Windows using Unetbootin's "frugal install" feature. Unfortunately, it only recognises my "/" drive, which Fedora resides on. My partitioning setup is:

* /dev/sda1: A 221GB NTFS partition which Windows will one day reside on.
* /dev/sda2-/dev/sda4: The partitions Fedora uses for its rather interesting disk management setup.
* /dev/sda5: A 10GB FAT32 partition that I tried to use as the boot drive for Unetbootin's frugal install. It didn't work.

What's wrong? Have I forgotten something? Or am I doing something completely wrong?

---

