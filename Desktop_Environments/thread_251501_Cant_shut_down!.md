---
title: "Cant shut down!"
date: 2006-09-05
forum: Desktop Environments
---

### Post by mister_p_1998 on 2006-09-05
Just put another drive in my son's Dapper machine, it was already installed with dapper from a machine at work, ran dpkg-reconfigure to see the video card, all runs well except it wont shut down! it just stops saying "will now halt" but screen & cpu still powered up. It was fine on the pc at work, any ideas guys?
Steve

---

### Post by Jussi Kukkonen on 2006-09-05
It's a bug. Shouldn't be dangerous, as everything that should get done seems to get done -- except the actual powerdown.
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/43961)

---

### Post by cotcot on 2006-09-05
It safe to power off the computer with this message. Your settings are saved.

---

### Post by doobit on 2006-09-05
> **cotcot said:**
> It safe to power off the computer with this message. Your settings are saved.

I put ```
acpi=force
``` in the boot command line of my GRUB menu.lst and it powers down every time now.

---

### Post by daiwai on 2006-09-05
Also make sure that ACPI is enabled in your BIOS.

---

