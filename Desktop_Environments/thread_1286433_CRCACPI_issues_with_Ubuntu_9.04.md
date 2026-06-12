---
title: "CRC/ACPI issues with Ubuntu 9.04"
date: 2009-10-09
forum: Desktop Environments
---

### Post by Keozon on 2009-10-09
I've been using Ubuntu (and its deviants) for years now on my laptop and other desktop, but this time, I'm in a pickle.

I have a RAID 0 being controlled by an LSI SAS3041E-R pci e controller. Ubuntu sees the device just fine, installs... and on reboots, either causes grub error 21, or lists a Firmware Glitch: powernow-k8: Your bios does not use ACPI-PSS something something

ACPI Aborted: CRC error

and a whole bunch of other info. All of it reusing the words CRC error. Cyclic redundency check, eh? That's data corruption, right?

So, I"ve reinitialized the drive, done everything I can think of, but still nothing. the drives check out individually and as a logical volume to WD Digital Lifeguard Tools. S.M.A.R.T. sounds the all clear. But, I get errors. And, things definitely don't load. I periodically get programs that report missing/corrupt files, simply don't launch, crash... the whole thing is totally unpleasant.

Any ideas on how to solve this problem?

---

