---
title: "Help with swap"
date: 2008-12-03
forum: General Help
---

### Post by jolly79 on 2008-12-03
Hi guys..

I just bought a 500gb drive, and clonede my old system drive with clonezilla.

so i movede a drive that was 160 gb to a 500 gig drive.

And everything is running fine.

BUT.... there is a lot of empty space on the drive.
And i have 4 partions on it .. home, swap, root and boot.

is it really not possile to create a 5 partiotion??

Another way would be to resize home, but swap is in the way, is it dangerous to delete swap from a live cd, and create it again?? (because it&#347; not possible to move it with gparted)

Hope to hear from you soon guys.. im loosing over 300gb here :-()

-Gutav

---

### Post by cariboo on 2008-12-03
There is no danger in removing swap, as you can't make any partition changes  with the partitions mounted.

Jim

---

### Post by jolly79 on 2008-12-03
Ok...

So load a live cd.. remove swap, and expand a partition and just create swap again.

And there shuld be no danger to my system in doing this??

---

### Post by PocketDog on 2008-12-03
Your splash screen will probably break, giving you a text-only boot. I don't know why that happens. It's easily fixed though

---

### Post by hyper_ch on 2008-12-03
you can have more than 4 partitions but only 4 primary partitions.

---

