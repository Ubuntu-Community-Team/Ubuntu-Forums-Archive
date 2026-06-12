---
title: "Promise fast trak PDC42819"
date: 2009-01-30
forum: General Help
---

### Post by srasiroslayer on 2009-01-30
Hello everyone,
i have a desktop machine running windows vista 64 bit. and operating system is installed on a RAID 0 array on two 500gb hdds.
to get to the point, without any notice, windows stopped loading.
it does boot, it gives me the options of last known good configuration, safe mode, etc....
but it fails to boot.
if i install the vista 64 bit dvd, and try to install it, the installation stops right after loading files.
now i know this is not a windows forum but give me some time to get to the point :)
if i disable the promise fast trak PDC42819 controller from the bios, the windows DVD loads properly and i can continue to install, but not on the controller.
so in order to be able to recover my files, i decided the best way is to grab my ubuntu CD and load it into live mode, copy my files to my other non-raid hdd running on the main sata controller.
i already know that my ubuntu won't see or recognise my raid setup, and i know that there is a chance all the files i installed on my raid setup may be gone but hear me out.
the two 500gb hdds are seagate barracudas and after testing them with the seagate diagnostic CD its turned out that they are fine.
and since windows does not boot randomly and relies on a boot loader also and a partition. and since it is booting to the point where it gives me my options, i assume that my files are indeed intact and recoverable.
another thing i would like to point out is that windows stopped booting after a normal windows restart.
so i would like to know is there a possible way i could load my fasttrak PDC42819 controller in a ubuntu live session, so i can mount the NTFS partition and copy the files i need to my other non raid hdd?
thank you

---

### Post by srasiroslayer on 2009-01-30
you may cancel this post,
problem fixed, i didn't use ubuntu though through the troubleshooting, luckily all my files were restored and the RAID array wasn't damaged.
i still find it awkward though that it didn't work.
thank alot.
you can cancel this post since its no longer related to ubuntu and/or linux.

---

