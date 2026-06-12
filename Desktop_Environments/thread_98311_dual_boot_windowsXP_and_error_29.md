---
title: "dual boot windowsXP and error 29"
date: 2005-12-02
forum: Desktop Environments
---

### Post by linuxNewb on 2005-12-02
I installed windows XP home, then I installed Ubuntu breezy on a new partition with GRUB. For some reason Ubuntu is listed twice like:

Ubuntu Linux??????-10-??????
Ubuntu Linux??????-10-?????? (Recovery Mode)
Ubuntu Linux??????-9-??????
Ubuntu Linux??????-9-?????? (Recovery Mode)

NOTE: '?' = dont remember, not actual question marks.

Anyway, Ubuntu loads fine, but when I select Windows XP Home I get:

ERROR 29: disk write error

Someone in another forum had the same problem. He stated that it turns out it was a 'bios protection' issue. He said he simply turned off the 'bios protection' and Windows booted fine. WHAT DOES THAT MEAN? Thanks in advance.

---

### Post by amohanty on 2005-12-02
Some BIOS manufacturers put virus protection in their BIOS' to make sure that the boot sector is not infected. Usually it will have a label like  ' BIOS Boot sector Virus Protection' or something like that in your BIOS setup.

Hunt for something like that and if it is on set it to off.

HTH
AM

---

### Post by linuxNewb on 2005-12-03
thx for the quick reply amohanty, turns out simply turning off the bios boot and setup passwords fixed the problem.

Also a side note: Windows will only start from a power-up on my Presario900 laptop if it was not the last OS to run. In other words if I boot Ubuntu, then select 'Restart Computer', then try to boot WindowsXP, windows hangs and won't start, I have to actually power-off first. Even the Windows installer hangs for the same reason.

---

### Post by amohanty on 2005-12-03
ANy messages as it hangs?

AM

---

### Post by elcu on 2006-01-06
I had the same problem.  In my case it was caused by the bootable flag being disabled on XP's partition.

- run 'sudo cfdisk <device>' (In my case, XP is installed on /dev/hda so <device> would be that)
- enable the bootable flag for the NTFS partition
- write changes
- quit
- reboot

Hopefully this fixes it for you.

---

