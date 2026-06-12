---
title: "Boot Repair failed fixing boot problem that appeared one day in a working system"
date: 2024-01-08
forum: Desktop Environments
---

### Post by victor2preston on 2024-01-08
I have Ubuntu 20.04 which recently stopped booting successfully. I've now rebooted from a USB  (I have 20.04 AND 22.04 on sticks, they both will succeed although they take a long time to boot.) When I booted off the 22.04 USB I tried running "install Ubuntu" which fails. I've now tried running "Boot Repair" which fails to complete (complaining that it cannot read or write to "dpkg", although it does not have and security settings that should present a problem, certainly not if running "sudo"). So I had it generate a Boot-Repair report which is at:

[https://paste.ubuntu.com/p/Y3N2gH3967]("https://paste.ubuntu.com/p/3YN2gH3967")

Can anyone help me, or do I need to send more information?

Thanks!

Victor

---

### Post by ajgreeny on 2024-01-08
Unfortunately your link takes me to:-
> 
The Paste you are looking for does not currently exist.
Return to the Pastebin

Can you check it and try again please

---

### Post by victor2preston on 2024-01-10
Sorry - typo in the link! But thanks for your fast response. The correct link is:

[https://paste.ubuntu.com/p/Y3N2gH3967]("https://paste.ubuntu.com/p/3YN2gH3967")

---

### Post by oldfred on 2024-01-10
Link still not working. What is shown is not the same as what it redirects you to.
But this does, is it yours?
[https://paste.ubuntu.com/p/Y3N2gH3967/](https://paste.ubuntu.com/p/Y3N2gH3967/)

Do not know RAID, but it looks like you are UEFI booting from sdf which is old MBR(msdos) partitioned.
You have mount of ESP - efi system partition in fstab. 
Ubuntu lets you use MBR, but UEFI highly recommends gpt which you have used for your RAID drives.
But you do not have any "ubuntu" entry for UEFI boot in UEFI. So grub not fully installed in UEFI mode.

You have an old grub in MBR of sde, which would have been for BIOS boot. Reinstalling or repairing in UEFI mode, made that obsolete.
Also what mode do you have as default boot mode in UEFI/BIOS settings?

Older versions of Ubuntu using Ubiquity installer, have wanted to install ESP to first drive or normally sda or first NVMe drive. So your SATA port/drive order on motherboard may also be an issue.  But reinstall of grub does let you correctly choose which drive to have boot files on. And BIOS install has always worked. BIOS/MBR not really recommended anymore. The only place for MBR is for an old system where you have Windows in BIOS boot mode.

---

