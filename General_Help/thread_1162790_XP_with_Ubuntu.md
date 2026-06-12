---
title: "XP with Ubuntu"
date: 2009-05-18
forum: General Help
---

### Post by ninos_loves_u@hotmail.com on 2009-05-18
im trying to dual-boot ubuntu with windows xp i have ubuntu already installed (9.04) and i was told that i need to create a new partition while installing windows xp but in the setup its showing me 2 partitions c: partition1 (unknown) (296387MB) and e: partition2 (unknown) (8856MB)
it wont let my create a new partition so i can install xp its asking be to delete the partition (windows xp cannot recognize the partition you selected, setup cannot install xp on this partition. howeever you can go back and delete the partition and then select the resulting unpartitioned space) <<< but that would format the whole drive or remove ubuntu wounded it? so can any1 help plz

---

### Post by Sashamaru on 2009-05-18
[[EMAIL="quote=ninos_loves_u@hotmail.com;7300420"]quote=ninos_loves_u@hotmail.com;7300420[/EMAIL]]im trying to dual-boot ubuntu with windows xp i have ubuntu already installed (9.04) and i was told that i need to create a new partition while installing windows xp but in the setup its showing me 2 partitions c: partition1 (unknown) (296387MB) and e: partition2 (unknown) (8856MB)
it wont let my create a new partition so i can install xp its asking be to delete the partition (windows xp cannot recognize the partition you selected, setup cannot install xp on this partition. howeever you can go back and delete the partition and then select the resulting unpartitioned space) <<< but that would format the whole drive or remove ubuntu wounded it? so can any1 help plz[/quote]


you have 2 HDD??? you can install windows on the whole disk (you can make a partition for format) and then install wubi..... i did that...

---

### Post by zvacet on 2009-05-18
```
sudo fdisk -l
```

Post output here.

---

