---
title: "partitions"
date: 2005-01-07
forum: General Help
---

### Post by ubuntunoob on 2005-01-07
how do i partition a fat 32 drive in XP?

---

### Post by Juergen on 2005-01-07
If it's FAT32 then there is already a partition on it.

If you want to change this partition you need either 3rd party tools for windows (like PartitionMagic) or try the free linux-equivalent parted, and since you'd probably like a GUI, qtparted.
I can't look ATM but strongly suspect that at least the QT-stuff isn't on the Ubuntu live CD (AFAIK Knoppix has it).

If you want to delete your partition and/or create new in XP, right-click on 'your computer' and choose 'administration' and then 'data media administration'

To install linux afterwards it's best to leave some free space and let the linux-installer create the partitions.

---

### Post by ubuntunoob on 2005-01-07
but when i put in the ubuntu live cd, it just boots from the cd and writes nothing to the HD. i wnated to make a partition to install ubuntu to but it wouldnt install

edit: dammit sorry i didnt realise that the live cd wasnt for installing and i should use the install iso instead.  :oops: well, hey im a noob

---

### Post by Juergen on 2005-01-07
That's the 'live' in live-CD, it's only meant to run from CD. 

Knoppix and other live-distros provide a script to install them onto the HD but for Ubuntu you need the 'install' CD. 
If you have to download another iso, I hope you're not on modem ;-)

---

### Post by ubuntunoob on 2005-01-07
yeah my bad i realised just before you posted so i edited

---

