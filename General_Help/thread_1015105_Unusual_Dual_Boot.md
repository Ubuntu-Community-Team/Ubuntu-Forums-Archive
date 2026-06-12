---
title: "Unusual Dual Boot"
date: 2008-12-18
forum: General Help
---

### Post by kasio on 2008-12-18
Hi,

I recently decided to install XP for video editing as I find Kdenlive slightly lacking. I have three hard drives and put XP on the third one. The problem is I installed XP without the other two plugged in, and when I plug them in, everything works as it should.

However, I cannot boot in XP using GRUB, and have to use the BIOS' boot menu to select the hard drive.  Is there a way to make GRUB boot XP?

---

### Post by logos34 on 2008-12-18
you'll have to use 'mapping' since windows is on another physical drive, [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

either

> title        Windows 95/98/Me
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

or 
> 
title        Windows 95/98/Me
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


---

### Post by kasio on 2008-12-18
Thanks, it worked fine.

---

