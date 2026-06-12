---
title: "Booting Ubuntu under windows"
date: 2009-05-24
forum: General Help
---

### Post by jorants on 2009-05-24
hi everyone,

i installed Ubuntu a wile ago.
i already had installed windows XP pro. and so i installed ubuntu on the side.
at this time ubuntu booted first and gave the chose witch system you wanted.
but my windows crashed and i had to reinstall it.
now windows boots and doesn't give the chose.

is there a way apart from reinstalling ubuntu) to get the ubuntu boot choce back?

tanx,

joran

---

### Post by themusicalduck on 2009-05-24
Follow this thread and it should fix everything:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by hal8000 on 2009-05-24
Well you've wiped grub from the MBR , not sure if youve erased your linux partitions. 
State which version of Ubuntu you use then boot with the live CD, post the output of

fdisk -l

This will show what partitions are left, if there is only a siingle partition you are reinstalling, if it shows more than one it may be just a matter of reinstalling grub into the mbr using the live CD. (This has been posted on the forum before) so lets see what partitions you have first.

---

