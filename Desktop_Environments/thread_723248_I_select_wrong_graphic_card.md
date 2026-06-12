---
title: "I select wrong graphic card"
date: 2008-03-13
forum: Desktop Environments
---

### Post by Sonah on 2008-03-13
I select wrong graphic card  

Now i can't see anything when  I  reboot ubuntu 7  :(

how can i Restore ?

please Help ..  


[IMG]http://img33.picoodle.com/img/img33/4/3/13/f_0ubuntum_90752f1.png[/IMG]

---

### Post by taurus on 2008-03-13
Boot into recovery mode from GRUB menu and reconfigure your X server again.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by Sonah on 2008-03-13
**Thanks Alot!    :)**

---

