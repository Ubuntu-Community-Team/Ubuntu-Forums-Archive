---
title: "Can't boot Dapper"
date: 2006-07-15
forum: Desktop Environments
---

### Post by wanton on 2006-07-15
Like the subject says...if it wasn't for dual-booting with MS, I'd have a paper-weight.

Anyway...the system:-
CPU Athlon 2000+
384 ish MB RAM
Dual-boot
hda 20GB Samsung (Ubuntu)
hdb 20GB IBM (Windows 98 )

No problems with anything for a very long time and that was just minor upgrade hassles, but it has never not booted.

This morning after selecting the 2.6.15-23-386 option from grub (it's the default, the one I alwasy use), my machine gets as far as:

"uncompressing linux.....ok booting the kernel"

Then no HD activity at all.

When I select the 2.6.15-23-386 (recovery mode) option

I get:
.
.
.
.
[4294667.384000] checking if image is initramfs...it is
[4294668.031000] freeing initrd memory: 6607k freed
[4294668.053000] ACPI: looking for DST ... not found!
[4294668.054000] ACPI setting ELCR to 0200 (from 0e08 )

Then all HD activity ceases and nothing happens.

I can boot from my Windows drive no worries.

Any ideas of where I should start looking?

TIA

---

