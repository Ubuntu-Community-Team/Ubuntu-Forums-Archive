---
title: "Restoring Windows' bootloader after uninstalling Ubuntu"
date: 2006-08-21
forum: Desktop Environments
---

### Post by Schalken on 2006-08-21
A friend of mine had Ubuntu on his computer along with Windows, however because all he uses his computer for is playing games and he was running out of space we decided to uninstal it.

We deleted Ubuntu's partition and sized up Windows, however we cannot boot. GRUB is still in the MBR. 

How do we get Windows' bootloader back into the MBR after deleting Ubuntu, so we can boot?

---

### Post by xtknight on 2006-08-21
With the XP recovery console try fixmbr (but don't do fixboot unless absolutely necessary).

I tried fixboot, and I believe what happened is with GRUB still in the boot record, the partition was misrecognized and all hell breaks lose when XP thought it was a FAT16 partition and overwrote the first 10MB of it!  I'm not sure if that's a problem if you just left GRUB on your MBR (and not accidentally on the boot loader of the XP partition).  If your XP can still boot from GRUB, you shouldn't experience this fixboot problem anyway (nor should you need to run fixboot).

---

### Post by bono on 2006-08-21
Same problem here.
Installed Ubuntu on other computer (I have 2 of them) and decided to delete Ubuntu from Windows computer.
I tried fixmbr - no use, didn't change a thing.
Had resize Ubuntu partition to minimum & leave it as it is - then installed fresh Windows...

Please help!  
  
 :confused:

---

### Post by bono on 2006-09-01
Problem solved for me :)
Did delete all partitions on HDD with PartitionMagic8.
& created new partitions with it...
Reinstalled Windows - boots just fine :)

---

### Post by FuriousLettuce on 2006-09-01
The best and easiest way to do it is to do what xtknight suggested.

Put in your XP disk, set your computer to boot from CD, and choose the recovery console from the options. After that, simply type 'fixmbr' (without quotes) in the console. Remove the disk and reboot, and XP should load up fine.

Much easier than deleting all your partitions & data!

---

