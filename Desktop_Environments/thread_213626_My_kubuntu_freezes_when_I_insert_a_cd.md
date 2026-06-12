---
title: "My kubuntu freezes when I insert a cd"
date: 2006-07-11
forum: Desktop Environments
---

### Post by frigopie on 2006-07-11
Hi, I have just installed a kubuntu dapper and it freezes when I insert a cdrom, or when I it boots whith a cdrom in. If a cdrom is in the system, when I boot the last message kubuntu throws is the one telling the hald is initializing. If I do a "killall hald" the system does not freeze when inserting a cdrom but I cant mount it... I had kubuntu Hoary and I had no problems of that kind...
any idea??

thanks...

---

### Post by frigopie on 2006-07-12
uuupp...

---

### Post by frigopie on 2006-07-12
up again...

---

### Post by frigopie on 2006-07-14
uuupp...

---

### Post by frigopie on 2006-07-14
I have solved it by disabling the dma in the cdrom drive putting it in /etc/hdparm.conf:

/dev/hdd{
   dma = off
}

And setting hdparm to start when the machine boots.

bye

---

