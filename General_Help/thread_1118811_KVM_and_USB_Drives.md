---
title: "KVM and USB Drives"
date: 2009-04-07
forum: General Help
---

### Post by pulseplanet on 2009-04-07
Hello All,

 I tried using a KVM switch (IOGEAR, gcs42uw6 , ) and noticed that my USB drives are not recogonised when I have the KVM plugged in. When I remove the KVM and restart the computer the external USB drives mount fine.

lsusb does not list the USB drives with the KVM switch. 
ls /dev/disk/[by-id/     by-label/  by-path/   by-uuid/] also do not show the drive.

dmesg output also does not show it with the KVM, but without the KVM everything seems ok. Any ideas, hints?

Linux PETDATA 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 GNU/Linux

Ubuntu 8.10

Thanks,
Karthik.

---

