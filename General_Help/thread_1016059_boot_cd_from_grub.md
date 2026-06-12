---
title: "boot cd from grub"
date: 2008-12-19
forum: General Help
---

### Post by TheLocalGraveDigger on 2008-12-19
while trying to resize a ntfs partition my computer got a hiccup. It seem the only way to repair it is with a windows xp installer, but my installer will get to the part were it says inspecting hardware and goes black for eternity(i think iv waited that long). My guess is that the installer is seeing my ext3 partition and is getting its mind blown away. I know grub can boot operating systems and hide partitions from them using the hide option, is it possible to do this with the installer CD for xp and hide the ext3 partition so it will repair the ntfs?

p.s. the drive is fine, the installer if fine,and the drive will still boot from the ext3 partition or a live CD so I'm sure its a software issue.

---

### Post by caljohnsmith on 2008-12-19
Fortunately, many people have been able to use a Windows Install CD with a HDD that has linux partitions on it, so I don't think that is your problem. At least in my experience, here are some reasons why the Windows CD may not recognize your HDD:
[LIST=1]
[*]The HDD's partition table is slightly corrupt
[*]If the drive is SATA, you will need to load special drivers for it while using the Windows CD or set your BIOS to use "IDE emulation" for the SATA drive
[*]BIOS settings for the HDD like maybe having "AHCI" enabled (try disabled)
[*]Having a RAID setup
[*]Trying to install to a HDD over 137 GB and the Windows Install CD doesn't have SP1 included
[/LIST]
If you don't think 2-5 apply to your setup, then I would at least check to see if the HDD's partition table is a problem, because that's easy to check. How about posting the output of:
```
sudo sfdisk -l
sudo fdisk -lu
sudo parted /dev/sda print
```
And we can go from there if you want.

---

