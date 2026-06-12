---
title: "Can't boot anymore diagnostics after installing ubuntu 8.10"
date: 2009-03-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pipposanta on 2009-03-07
Hi,
I succesfully installed ubuntu 8.10 on my dell mini 9 but now I can't access diagnostics partition anymore. I didn't delete the partition during ubuntu installation but now when I press 0 during boot and select the diagnostics option it boots ubuntu.

Is there a way to make the diagnostics work again?

Thanks in advance!!

---

### Post by albandy on 2009-03-07
add the partition to grub as it were a windows partition

---

### Post by pipposanta on 2009-03-07
How can I do this?

---

### Post by albandy on 2009-03-07
add this entry to your /boot/grub/menu.lst file:



title Diagnostics Partition
root (hd0,0)  #change (hd0,0) to your diganostic partition number
savedefault
makeactive
chainloader +1


-------------
hd(0,0) means first hard disk 1st partition
hd(0,1) means first hard disk 2nd partition
hd(0,2) means first hard disk 3th partition

---

### Post by pipposanta on 2009-03-07
So there is not a method to boot the diagnostic from the menu that I call with the 0 key at the boot? The bios menu instead of grub.

---

