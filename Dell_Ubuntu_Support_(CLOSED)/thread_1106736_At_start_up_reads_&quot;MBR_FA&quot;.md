---
title: "At start up reads &quot;MBR: FA&quot;"
date: 2009-03-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xoftware on 2009-03-26
When my dell mini 9 starts to boot, and it reaches the master boot record instead of just starting the grub boot loader right away, I get on the screen "MBR FA:" I have to then hit the (a) key and then the screen displays "MBR 1234F:" . From there I have to push the (2) key(if I push (1) it puts me in a dell hardware diagnostic prompt and if I push (3) or (4) it just goes to the next line reads "MBR FA:" again), and then it starts ubuntu, though sometimes it will start without the key board or mouse working. I would like to know how to get it to boot directly without the "MBR FA:" screen and with the keyboard and mouse working. I messed around with the root access and formatted an external hard drive before I had the problem, so that might be the cause. Any help would be much appreciated, thanks!

---

### Post by ugm6hr on 2009-03-28
Perhaps if you explain exactly what you did?

Also, post the contents of: /boot/grub/menu.lst

---

### Post by xoftware on 2009-03-28
I actually figured it out. When I partitioned the external hard drive, I accidently undid the "boot" flag on my file system partition. Once I flagged the partition with my file system as boot, my computer started up just fine. So if you see MBR FA: after BIOS start up it has something to do with flags on your partition. Anyways, thanks for help.

---

