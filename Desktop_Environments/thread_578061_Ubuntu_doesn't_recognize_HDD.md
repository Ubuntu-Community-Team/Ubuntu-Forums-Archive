---
title: "Ubuntu doesn't recognize HDD"
date: 2007-10-16
forum: Desktop Environments
---

### Post by jdunk90 on 2007-10-16
I can boot Ubuntu with the CD and use it, but I can't install it to my hard drive because it doesn't recoqnize it.  This computer is a new build, but the HDD shows up in BIOS.  Any suggestions on how to get Ubuntu to recognize my drive?

---

### Post by lonelyxpeople on 2007-10-16
this may seem a bit redundant, but you should check the jumper settings, if you can, and make sure it set to a master/slave (whichever you need or want) or single drive setting.




also, you may get more help easily if you specify the kind of drive.
i.e. a Seagate 200gb SATA drive, etc.


welcome to linux. :p

---

### Post by jdunk90 on 2007-10-17
The hard drive is SATA so I don't think I have to mess with jumpers if I read correctly.

---

### Post by mumushi on 2007-10-17
the only thing that makes your HDD not recognize is the setting. You can always see it in your bios. Make it the primary master and im sure things will be ok.

---

### Post by jvittetoe on 2008-05-04
hi, im having the same issue here. i have 1 HDD, 320GB, i have about 220 of that NTFS for my windows OS, and the rest is ext3 and swap. i formatted those within windows partion magic 8. when i reboot to the live cd and i come to the ubuntu desktop. when i double clikc to install, i come to the partition phase. ubuntu can not recognize my HDD. it is a SATA drive and i have it plugged into the SATA1 slot on my mobo. when i come into BIOS, i see it is set as IDE Channel 2 Master. Does that need to be on Channel 0 Master? Im not sure what to do.

---

