---
title: "pppoe internet sharing"
date: 2008-08-04
forum: Debian
---

### Post by CosminGC on 2008-08-04
hi, I am testing debian and it's great, but if with ubuntu the internet sharing thing I made it with firestarter with debian it does not work. I was wondering if there is a howto for the pppoe internet sharing like [this one for gentoo]("http://www.gentoo.org/doc/en/home-router-howto.xml").

Thanks.

---

### Post by Bachstelze on 2008-08-04
You can use this one, it uses iptables and dnsmasq, which are available in Debian as well. Of course, you'll have to install dnsmasq with apt-get instead of emerge, but all the iptables configuration part is the same.

Try it, and feel free to post back if there's a specific step you can't reproduce ;)

---

