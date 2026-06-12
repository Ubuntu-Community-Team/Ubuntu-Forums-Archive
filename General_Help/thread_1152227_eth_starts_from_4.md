---
title: "eth starts from 4?"
date: 2009-05-07
forum: General Help
---

### Post by firsttimeuser on 2009-05-07
Just fresh installed a ubuntu 64 server which has 4 eth ports. 

And few seconds ago I noticed the eth starts from 4, when I do ifconfig -a, it list the eth ports as 

eth4
eth5
eth6
eth7

what is the deal? What files should I modify to change the number from 0 to 3?

Thanks

---

### Post by Alterax on 2009-05-07
No trouble at all.  The settings are in /etc/udev/rules.d/70-persistent-net.rules  Just alter those as you see necessary.

---

### Post by firsttimeuser on 2009-05-07
thanks, it works!

and any idea why this happened?

---

