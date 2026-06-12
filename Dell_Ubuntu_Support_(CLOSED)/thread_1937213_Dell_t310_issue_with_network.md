---
title: "Dell t310 issue with network"
date: 2012-03-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hescominsoon on 2012-03-07
I have the 10.04 lts installed x64.  Dell t310 with 16 gigs ram.  2 broadcom gig-e internal and two quad intel pci-e cards.  if i leave the machine sitting for a few minutes the eth 0(broadcom zero) stops allowing traffic.  physical connection is fine.  but i cannot ping or anything else form outside the box to the inside.  If i do a ping from the console of the server thee's a second delay while the nic is apparently reactivated.  Once that occurs outside pings and connections are once again accepted.  I've updated all firmware...latest updates to the ubuntu....power management in the bios is shutoff.  I'm at a total loss.  any ideas?

---

### Post by hescominsoon on 2012-03-07
I tried an /etc/init.d/networking restart and saw an error:
siocdelrt no such process
along with a postfix file error.  i uninstalled postfix and modified my hosts file to remove ip6 references since i am not using ipv6.  I issued the networking restart again.  no errors.  Will see if the networking stays up this time.

---

### Post by hescominsoon on 2012-03-07
nopers after about 5 minutes i loose external connectivity...it used to work fine..i am curious what has changed with ubuntu 10.04 lts lately.

---

