---
title: "boot flag changes after booting to windows"
date: 2009-01-18
forum: General Help
---

### Post by lavinog on 2009-01-18
I recently erased and reinstalled my windows XP partition to add native ahci support.
I have a three primary partitions: boot, linux-swap, and windows
I have a three logical volumes: ubuntu root, home, and a misc storage
before I had the boot partition set with the boot flag, and grub will let me access windows, and ubuntu.
After reinstalling windows, I can boot fine with grub into windows, but windows changes the boot flag to be set to the windows partition. This will let windows and only windows to boot. 
I have to boot with a live linux cd and set the boot flag back to my boot partition to get grub to boot normally. I have to do this every time after booting into windows.

I originally installed windows after ubuntu, and don't recall having this issue.

---

### Post by lavinog on 2009-01-18
solved it
i needed to install grub to the mbr and not to the partition.
in grub terminal:
root(hd0,0)
setup(hd0)

i was doing setup(hd0,0)

---

