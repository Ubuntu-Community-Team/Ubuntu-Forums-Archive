---
title: "How to Stop GRUB changing my active partition"
date: 2009-01-04
forum: General Help
---

### Post by aleangelico on 2009-01-04
I have a dual boot Grub for linux/vista. Every time I boot Linux, this becames my active partition. When I boot vista, everything works fine, except the hibernation. 

I found an old thread but I cannot post there (because is old) here: [http://ubuntuforums.org/showthread.php?t=582849](http://ubuntuforums.org/showthread.php?t=582849)

So, the solution to be able to hibernate Vista is open the disk manager (in vista) and make the Vista partition active. Is there a way to stop grub for changing the active partition so I don't have to change it every time?

Thanks
.alex

---

### Post by caljohnsmith on 2009-01-04
How about first opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And find any entries that use the line "makeactive", and delete those lines. Then Grub shouldn't change the boot flag on any of your partitions. Let me know how that goes or if you run into problems.

---

