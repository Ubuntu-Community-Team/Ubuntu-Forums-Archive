---
title: "Reinstalling windows w/ my dual boot setup"
date: 2009-05-03
forum: General Help
---

### Post by CynicalPsycho on 2009-05-03
If I wipe my win partition and reinstall windows will it affect my Ubuntu?

I'm guessing yes, which is why I also wonder if there is a simple method i can use to backup my current ubuntu configuration and reinstall ubuntu with after I've reconfigured my windows...

---

### Post by Melk79 on 2009-05-03
Yes, I believe if you reinstall Windows it will wipe the whole HDD.  Microsoft, not surprisingly, isn't as accomodating in this regard.  I'm not sure which Ubuntu version you're running, but 8.10 and 9.04 have a USB disk creator from System>Administration that would keep your settings.  I think you would still need to backup your data though.  Haven't used that myself yet.

---

### Post by lisati on 2009-05-03
When I've reinstalled Windows using a recovery partition/DVD I've normally been able to do so without wiping Ubuntu (it sometimes means looking for an option to not alter the partition layout), but grub (Ubuntu's bootloader) usually gets nuked in the process. If you have an Ubuntu "Live CD" it's usually fairly easy to reinstate grub. (I'm going to have to do so myself on one of my machines soon, after getting XP bootable nuked grub)

---

