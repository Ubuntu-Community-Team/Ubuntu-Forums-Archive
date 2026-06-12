---
title: "partitions disappear"
date: 2009-03-18
forum: General Help
---

### Post by Rita G. on 2009-03-18
hi sweeties,

want to resize a partition on hdd....

but now gparted shows my once “beautifully” partitioned hdd

as one whole unallocated partition.

anybody know how to get out of this mess?

---

### Post by =Planta= on 2009-03-19
Hello,

I'm hoping it's not too late. :-|

Just a quick brainstorming.
If... 
[LIST=1]
[*] ...you have **not** turned off / restarted your computer **since** your GParted accident
[*] ...you have **not** unplugged / replugged the HDD (if it is external) **since** your GParted accident
[*] You had your HDD partitions mounted **before** your GParted accident
[/LIST]
Then :
[LIST]
[*] Your system still sees your HDD considering its pre-accident MBR, so you have the chance to mount whatever umounted partitions and backup everything (to external HDDs, DVDs, remote computers, etc), in the first place.
[*] The command **$ df** should show how many 1K-blocks each partition has, allowing you to attempt a manual rebuild of your HDD's MBR using fdisk (mind the "u" fdisk command, which changes the displayed units from cylinders to sectors, perhaps making calculations easier when you have to specify the partition's size)
[/LIST]

Just checking silly stuff:
[LIST]
[*] Has GParted really applied these "partition disappearing" changes?
[*] Does by any chance **$fdisk -l** display your old "beautiful partitioning" (<- :) heh)?
[/LIST]

Oh well, best of luck..
Planta.

---

### Post by Rita G. on 2009-03-26
anybody else?

---

