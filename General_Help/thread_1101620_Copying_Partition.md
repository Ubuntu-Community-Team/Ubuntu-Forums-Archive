---
title: "Copying Partition"
date: 2009-03-20
forum: General Help
---

### Post by Jameshardy88 on 2009-03-20
Hi i currently have a tri-boot system of Xp, Ubuntu 8.10 (my normal OS) and ultimate edition (which i have been experimenting with.

Basically i want to know if i can copy the ultimate edition partition and put it on my external hard drive,freeing up space on my internal HD. Would i then when plugging in my external HD be able to access the operating system (with all the changes etc i have made)??

thakns for any help

James

---

### Post by Jameshardy88 on 2009-03-20
-

---

### Post by Jameshardy88 on 2009-03-21
-

---

### Post by bumanie on 2009-03-21
If I get what you want to do, you should be able copy it to an external HDD. If you want to boot from that, it would be best to have a bios that includes usb-HDD booting.
I just made an external usb-HDD that boots when bios is set to boot from usb-HDD. I installed ubuntu on it and set grub to (hd0,0) - it boots fine. I assume if you copy ultimate edition and have a bios that has a boot from usb-HDD setting, as long as you edit /boot/grub/menu.lst to (hd0,0) it should work. If you go [here]("http://users.bigpond.net.au/hermanzone/p15.htm") and are prepared to read, Herman has heaps of grub and booting info. He may have something more specific to your needs, but I had success as noted above.

---

### Post by Klaz168 on 2009-03-21
Use gparted, you'll first need to make some free space on the new HDD, then copy the existing partition to the unallocated free space on the new HDD.

Then to access watever OS you have on the new HDD, you'll need to edit your menu.lst located at /boot/grub.

Hope that helps.

---

### Post by Jameshardy88 on 2009-03-21
Thanks very much guys =)

---

### Post by Jameshardy88 on 2009-03-21
I've tried copying it using Gparted however it says there has been an error in copying it over once it completes the process and the nothing appears in the new partition. Does anyone know what may causing copying a partition to fail?

---

