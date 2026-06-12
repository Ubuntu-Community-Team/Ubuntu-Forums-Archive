---
title: "nvidia drivers"
date: 2006-09-14
forum: Desktop Environments
---

### Post by basvg on 2006-09-14
Hi all,

I just did another update of my Dapper box, kernel-update so had to reboot. After booting, no X. Luckily I had a laptop to surf the Web a bit. After consulting the forum and IRC I tried several things:

- reinstall kernel + restricted modules
- reinstall nvidia stuff by following the wiki-page
- run modprobe

It didn't seem to fix the problem. I switched the driver to 'nv' (found that tip on another thread here) and now I'm at least able to log into X again. The last bit of info that I found comes from dmesg:

[17180659.268000] nvidia: disagrees about version of symbol boot_cpu_data
[17180659.268000] nvidia: Unknown symbol boot_cpu_data

I googled for this but that doesn't help me much. Any help in resolving this is greatly appreciated.

Cheers

  Bas

---

