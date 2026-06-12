---
title: "Grub Problem with 3 HDD"
date: 2006-07-08
forum: Desktop Environments
---

### Post by fabioleroy on 2006-07-08
Hi all,

I have a problem with the installation of GRUB.
On my motherboard (DFI LanParty nForce4 SLI Expert, with 4 Sata Channels + 4 Sata Channels on Silicon Image 3114), I have 2 Sata HDD in the channels of the chipset NF4, in RAID 0 with Windows XP installed, and 1 Sata HDD in the channel of Silicon Image controller.
I have to install Ubuntu in the HDD on Silicon Image Controller and I want to install GRUB in the MBR of this HDD, but the Ubuntu installer install GRUB in the MBR of the first of 2 Raid Disks and Ubuntu and Windows don't start! :( (I have in this case to fix the windows MBR with the windows console recovery to start windows)
How can I install GRUB in a specified position with the ubuntu installer?

Thanks in advance,

BYEZ!

---

