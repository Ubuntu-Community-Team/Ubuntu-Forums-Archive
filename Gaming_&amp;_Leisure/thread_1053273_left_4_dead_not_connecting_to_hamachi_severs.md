---
title: "left 4 dead not connecting to hamachi severs"
date: 2009-01-28
forum: Gaming &amp; Leisure
---

### Post by c/Kr3t on 2009-01-28
i've joined a few hamachi networks to play left 4 dead on a private server and when i put into the console connect IP-ADDRESS it hangs on the loading screen and kicks back saying couldn't connect after 10 retries.

is it my network that is messing up or theirs?

---

### Post by c/Kr3t on 2009-01-28
i'm using this page [http://www.supware.net/HamachiUbuntuHowto/](http://www.supware.net/HamachiUbuntuHowto/) to do it, i'm at the bottom where it talks about adding and removing the ham0 line.  i added the line 

route add -net 5.0.0.0 gw 5.100.97.114 netmask 255.0.0.0 dev ham0

and deleted 

route del -net 5.0.0.0 gw 0.0.0.0 netmask 255.0.0.0 dev ham0

but when i go back to route -n it reverts back to 
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0

---

