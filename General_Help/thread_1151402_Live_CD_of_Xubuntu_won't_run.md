---
title: "Live CD of Xubuntu won't run????"
date: 2009-05-06
forum: General Help
---

### Post by K8JWT on 2009-05-06
I just made a LiveCD of Ubuntu and Xubuntu to try out on a older laptop I was given and both of the start to load up but then I get the following error message.

[   60.205812] Buffer I/O error on device sr0, logical block 228664


The number on the end raises incrementally as it continus to try to load.

Laptop is a Gateway Solo 9300 with 160Mb of ram, 20Gb Hard drive.

Have tried the same LiveCD's in another modern desktop computer and get similar errors.

---

### Post by zvacet on 2009-05-07
Did you check **md5sum** and **disc integrity**?You will find instructions how to do it [here.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by Promethalus on 2009-05-07
dude, the cpu that come`s with that laptop, is not so very good, it is just unable to run ubuntu, [http://support.gateway.com/s/Mobile/Solo_Series/P9300/p930017.shtml](http://support.gateway.com/s/Mobile/Solo_Series/P9300/p930017.shtml)

you see? just compare it with the minimal specs required for ubuntu

---

### Post by raymer on 2009-05-08
> **Promethalus said:**
> dude, the cpu that come`s with that laptop, is not so very good, it is just unable to run ubuntu, [http://support.gateway.com/s/Mobile/Solo_Series/P9300/p930017.shtml](http://support.gateway.com/s/Mobile/Solo_Series/P9300/p930017.shtml)
 
you see? just compare it with the minimal specs required for ubuntu
 
Um, I have a gateway 9300 here with PII 400mhz and I have been using it with xubuntu versions through 8.10 for quite some time. I had to tweak it by removing unneeded processes, but with 280MB of RAM it functions passably as my TV in the bedroom.
 
However, upgrading to 9.04 I found the same issue as the OP. So, does 9.04 raise the bar as far as minimum required CPU?
 
-Ray

---

