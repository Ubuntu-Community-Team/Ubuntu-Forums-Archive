---
title: "please help: HAL no longer working (6.06.1)"
date: 2006-09-28
forum: Desktop Environments
---

### Post by Poldi on 2006-09-28
hi, guys.

this is Ubuntu (Gnome) 6.06.1 with only the official repos, no backports and quite fresh (installed 10 days ago) on an IBM Thinkpad R40 (1,4GHz Centrino, 512 MByte, internal DVD r/w  drive).

after my latest boot HAL no longer detects media insertion or drives connected to the machine.

in my 'Computer' folder in Nautilus I see the entry for root plus 5 'generic' media type-drives (compact-flah, memory-stick, SD/MMC, SmartMedia and CD/DVD). the only really attached drive is the internal DVD. 

if I manually mount an inserted CD via Nautilus it does work and the medium is accessible, but upun eject I loose the drives icon completely and can no longer access a CD graphically at all until the next reboot.

this all happens weather I have a CD inserted at boot or not.

apt is up to date.

any suggestions? this looks like some config file is broken/gone/locked and HAL does use some defaults instead. but automatic discovery of any kind does just not happen.

plead help.

kind regards,
Carsten

---

