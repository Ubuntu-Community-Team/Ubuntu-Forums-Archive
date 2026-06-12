---
title: "Ubuntu non-RAID, Vista RAID - Grub HELP?"
date: 2009-02-03
forum: General Help
---

### Post by GoofusGreen on 2009-02-03
My desktop has two 250-GB drives in RAID and one 500-GB non-RAID drive. My Vista partition is on the RAID drives and Ubuntu is on the non-RAID.

I tried using the lastest text-based installer, which recognized the Vista partition at GRUB install time. Unfortunately, it didn't add a Vista entry to menu.lst .

FakeRaidHowTo applies to installing Ubuntu onto RAID, but I would like to add a Windows on RAID entry to GRUB.

dmraid is installed fine. the entry to /dev/mapper/ is there. Actually, there are two: isw_chechedfdfVolume0 and isw_chechedfdfVolume01

I can mount the RAID partition from command-line just fine also.

Also, by going through BIOS I can boot from one disk or the other to choose between Windows and Ubuntu.

---

