---
title: "Can't change brightness Ubuntu 13"
date: 2013-05-29
forum: Desktop Environments
---

### Post by Heinzelmannchen on 2013-05-29
I recently updated to ubuntu 13.04 and needed to change the brightness because i was getting a blank screen on login. FN+UP temporarily fixed this.

i entered the following in /etc/default/grub

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux acpi_backlight=vendor"
```

and that fixed the blank screen problem but now i can change the brightness. how can i make it so i can change the brightness settings again?

---

### Post by Toz on 2013-05-29
What is the make/model of your computer and what video card(s) and drivers do you have? This might help:
```
sudo lspci -vnn | grep -A12 VGA
```

(Stab in the dark) You might want to try:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""
```
...instead of "acpi_osi=linux acpi_backlight=vendor". It seems to be a valid workaround for newer devices. As a reminder, make sure you run "sudo update-grub" afterwards to commit the change to grub.

---

### Post by Heinzelmannchen on 2013-05-29
> **Toz said:**
> What is the make/model of your computer and what video card(s) and drivers do you have? This might help:
```
sudo lspci -vnn | grep -A12 VGA
```

(Stab in the dark) You might want to try:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""
```
...instead of "acpi_osi=linux acpi_backlight=vendor". It seems to be a valid workaround for newer devices. As a reminder, make sure you run "sudo update-grub" afterwards to commit the change to grub.

Sorry about that. I have lenovo g580

here is ```
sudo lspci -vnn | grep -A12 VGA
```


00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])

---

### Post by Toz on 2013-05-29
Did you try the acpi_osi=\"!Windows 2012\" kernel boot parameter?

---

### Post by Heinzelmannchen on 2013-05-29
Yes i tried entering that then updated grub. After restarting i'm still not able to change brightness.

---

### Post by Toz on 2013-05-29
Can you post back the results of:
```
cat /proc/cmdline
```
...after booting with the acpi_osi=\"!Windows 2012\" kernel boot parameter? 

Also, can you post back the contents of your dmesg log file like this:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

You might also want to try each of the existing ones separately:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

---

### Post by Heinzelmannchen on 2013-05-29
```
cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=37d6764d-d42f-4b4b-a693-7579383559fb ro quiet splash acpi_osi=linux acpi_backlight=vendor vt.handoff=7


[URL="http://paste.ubuntu.com/5715163/"]Pastebin
[/URL]

---

### Post by Heinzelmannchen on 2013-05-29
The following works
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"
```

Thanks for the support. I always feel so dumb when i can't figure this stuff out on my own.
I couldn't find much on the subject when searching, maybe i didn't look hard enough. Oh well i really appreciate your help =).

---

### Post by arthurborsboom2 on 2013-10-21
I confirm that on a Acer Aspire V5-171 (Intel 3rd generation i915), the above statement got the brightness controls working again.

Ubuntu 13.10 x64
Kernel: 3.11.6

---

