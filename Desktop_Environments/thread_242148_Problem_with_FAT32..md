---
title: "Problem with FAT32."
date: 2006-08-23
forum: Desktop Environments
---

### Post by BoomAM on 2006-08-23
Hi.
Ive just nuked my HDD and set it up as follows:
20Gb Ubuntu
2Gb swap.
30Gb FAT32 Storage
40Gb Vista.

Im having problems with the FAT32 storage though. I created the FAT32 partition and formatted it through gparted. I planned on having it as a common storage between Ubuntu & Vista. 
But everytime i try to access it, it says it cant access it, saying something about pmount (im at work atm, otherwise i'd be more specific).
So i setup a mount point for it, it then opens the drive, but i cant do anything with it?

Ideas?

---

### Post by mc^2 on 2006-08-23
It's just a guess: 
Go to: System->Administration->Disks (gksu disks-admin) and try to browse the partition (maybe you'll have to enable it first). If it's not possible, I'm at a loss. If you manage to do it add a line like:
/dev/sda6  [tab]     /media/fat [tab]     vfat    [tab] defaults,utf8,umask=007,gid=46 [tab] 0  [tab]     1
to your /etc/fstab (this one's mine, it's working) and it should be allright.

---

### Post by BoomAM on 2006-08-23
No difference.
Ive noticed that everytime i do something in Gparted, it keeps erroring saying that 'At least one operation was applied to a busy device'. Im asuming that its saying that because Ubuntu is booting off the same HDD thats being edited?

---

### Post by mc^2 on 2006-08-24
but can you see the partition in System->Administration->Disks?

---

### Post by BoomAM on 2006-08-24
nm now. 
Fixed it. :)

Thanks for the help though guys/gals. :)

---

