---
title: "Brightness slider missing + issues"
date: 2016-05-28
forum: Desktop Environments
---

### Post by ilkkah on 2016-05-28
Hi,

So, the brightness slider is missing. I'm running Ubuntu 16.04, and:

```
ile@pc:~$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550]
    Subsystem: ASUSTeK Computer Inc. RV710 [Radeon HD 4350/4550]
    Kernel driver in use: radeon
    Kernel modules: radeon


```

```
ile@pc:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-4.4.0-22-generic root=UUID=f6ae90a1-408b-447d-818a-3dea7d981ed7 ro acpi_backlight=vendor quiet splash vt.handoff=7


```

```
ile@pc:~$ ls /sys/class/backlight/
ile@pc:~$ 


```

I can change the brightness with:

```
ile@pc:~$ xrandr --output DVI-0 --brightness 0.7

```

... but it doesn't work perfectly: sometimes the brightness changes back to "1" randomly afterwards (or maybe something triggers it, not sure).

Wonder how to solve this?

---

