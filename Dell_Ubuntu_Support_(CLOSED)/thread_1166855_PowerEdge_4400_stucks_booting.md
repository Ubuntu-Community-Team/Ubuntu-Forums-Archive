---
title: "PowerEdge 4400 stucks booting"
date: 2009-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cintaroja on 2009-05-22
Hi, I'm trying to install ubuntu 8.04.2 Server on a P0weredge 4400 server...I installed it indeed, but when I try to boot the server stops before booting ubuntu and after the "BIOS Installed Succesfully" message, it gives me "Strike F1 to retry boot F2 for setup utility" . The RAID drivers are present and loaded (Container 1: 17 Gb, Optimal. Container 2: 69.8 Gb Optimal), and if I try to reinstall, ubuntu CD detects another installation of Ubuntu (the first one I installed).

Is there any issue with this server I don't know? Does anybody can help meeee, pleaseeeee!!!!

Thanks

---

### Post by coffeeaddict22 on 2009-05-23
Hi,
I'm not a guru, but if you aren't getting to the GRUB menu then you've got problems with the bootloader... the only issue I know of that does this (and that DOESN'T mean there aren't a ton of others, just that I'm experience- deprived) is you've changed your boot options in the BIOS to CD/ whatever, and now it can't boot off the HDD because you aren't letting it.  Most common is a USB key of course, but you'd have checked for that I assume.

---

### Post by cintaroja on 2009-05-23
> **coffeeaddict22 said:**
> Hi,
I'm not a guru, but if you aren't getting to the GRUB menu then you've got problems with the bootloader... the only issue I know of that does this (and that DOESN'T mean there aren't a ton of others, just that I'm experience- deprived) is you've changed your boot options in the BIOS to CD/ whatever, and now it can't boot off the HDD because you aren't letting it.  Most common is a USB key of course, but you'd have checked for that I assume.

Hi coffeaddict, I have thought the same but I have tried either the manual installation first and the guided after, leaving ubuntu installs itself wherever it wants (guessing it wasn't finding the boot, cause I have RAID 5 and RAID 1 on it). Also I've tried changing the boot options in the BIOS,and the isuue with the USB key is that the machine is old and has only the CD os HDD boot option.
However I have spoke with a DELL support agent that sent me a centOS Live CD and a .bin file to upgrade the firmware because even if ubuntu it's not supported for this Poweredge 4400, the firmware upgrade could solve the problem. I'll try on Monday...will report here anyway.
Thanks a lot...

---

### Post by cintaroja on 2009-06-02
Heyyyyyy, SOLVED....
I don't know what was the problem exactly, but when I format all drives and started a new installation using the RAID1 to install the operative system and the RAID5 for the /var/ directory, it works!!!!
Thank you for your help and interest...
Even Dell server support didn't know what was the issue (they don't support Ubuntu).

Javi

---

