---
title: "howto disable LUkS?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by rupert on 2006-07-26
Hi,
i have some encrypted disks with keyfiles, since I cant get thm to work with an entry in crypttab i decided to manage them manually via shellscripts,


So how can I disable the passwords request windows when gnome start?

Another annoying thing is that I set the encrypted devices to noauto, but while booting the kernel complains that it cant find the device, i thought noauto means that its untouched until i need it.
On boot cryptdisks says something about an insecure mode, but the keys are set to read only, and the ,mapper device is not created.

crypttab:
Daten 		/dev/sda1 /var/local/http.o  luks,retry=3,cipher=aes-cbc-essiv:sha256
fstab:
/dev/mapper/Daten       /media/DATEN    ext3    user,noauto        0       2

any hope there?

---

