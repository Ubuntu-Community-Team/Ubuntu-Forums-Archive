---
title: "converting xp disk image to vdi"
date: 2008-12-18
forum: General Help
---

### Post by sigurnjak on 2008-12-18
I was converting xp disk image to vdi and now i have a little problem .
vbox tells me file is too large !


Converting VDI: from DD image file="/home/user/xp.dd" to file="/media/disk/xp.vdi"...
Creating dynamic image with size 81948432384 bytes (78153MB)...
Failed (VERR_FILE_TOO_BIG)!
andrey@andrey-desktop:~$ 



 What can i do to now ?  :confused:

---

### Post by sigurnjak on 2008-12-18
Oh , never mind ! I was moving it to a FAT hd which can only handle files up to 4 gig . Now i partitioned my hd to ext3  and all is well .:lolflag:

---

