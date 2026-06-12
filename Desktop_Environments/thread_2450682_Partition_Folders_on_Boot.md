---
title: "Partition Folders on Boot"
date: 2020-09-18
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-09-18
Ubuntu 18:04 LTS

Folks, system working fine but for some reason I have four folders that appear when started showing contents of different partitions.

None of the folders appear in fstab or mtab so I am not sure where they are being produced from.

> From my file manager I get the following;

/dev/dm-1   
/dev/dm-2
/dev/sda3       
/dev/sda6   


It is a tri-boot system with Ubuntu my main system on /dev/sda5
Windows10 on /dev/sda3
Fedora on a LVM system on /dev/sda7 (Think that is dm-1 and dm-2)

/dev/sda6 I am not sure of, it contains boot and efi files but my efi partition is actually /dev/sda1

My question really is; where might these folders be being created?

Geoff

---

### Post by TheFu on 2020-09-18
when you type **df -Th **do they show in the list?  If not, then they aren't mounted and whatever GUI  is showing them is at fault.

---

### Post by CelticWarrior on 2020-09-18
> [COLOR=#000000]/dev/sda6 I am not sure of, it contains boot and efi files but my efi partition is actually /dev/sda1[/COLOR]


Very likely it's Fedora's /boot partition.

---

### Post by Geoff_Lane on 2020-09-21
> **CelticWarrior said:**
> Very likely it's Fedora's /boot partition.

Yes, could be, none if the drives are issues, just curiosity as I know automounts are generally in fstab or mtab

Geoff

---

### Post by Geoff_Lane on 2020-09-21
> **TheFu said:**
> when you type **df -Th **do they show in the list?  If not, then they aren't mounted and whatever GUI  is showing them is at fault.

No, they don't show with that command, only sda1 and sda5  (efi partition and Ubuntu system) are mounted prefixed by /dev.  Loads of loops and a few tmpfs show and I know of them.

Thanks for info TheFu - if I right click mouse over icon in task bar I can unlock from launcher so that is where they are being launched from.  Not sure what config file controls that.

Geoff

---

