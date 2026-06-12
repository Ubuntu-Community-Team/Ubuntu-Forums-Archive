---
title: "Made the upgrade to x86_64, now to delete 32bit partition...."
date: 2009-03-06
forum: General Help
---

### Post by mªrty on 2009-03-06
Hi all, I've successfully made the transition to 64 bit and it's working well! Now I want to get rid of my 32bit ubuntu install. My hard drive is partitioned like:

[LIST=1]
[*]ubuntu 32bit (installed first),  about 5GB
[*]ubuntu 64bit (installed later),  about 10GB
[*]old '/home' partition,  about 60GB
[*]swap,  1GB
[/LIST]

What can I do to delete my 1st partition? What I'm thinking right now is to boot to LiveCD, delete 1st partition & hope GRUB remains intact, will this work?

---

### Post by taurus on 2009-03-06
If you install Ubuntu x86_64 last, then GRUB will look for /boot/grub/menu.lst in that partition.  Therefore, you can remove the i686 version from your harddrive.  But if you have a problem booting after removing the 32bit version, you can reinstall GRUB to MBR again.  Just make sure you have a working /boot/grub/menu.lst (on your x86_64).

---

### Post by mªrty on 2009-03-06
Thank you, taurus :)

I do have /boot/grub/menu.lst, I'll come back and reply once I've deleted the ubuntu 32bit partition.

---

