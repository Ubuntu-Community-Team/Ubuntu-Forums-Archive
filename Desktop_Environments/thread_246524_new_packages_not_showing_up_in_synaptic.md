---
title: "new packages not showing up in synaptic"
date: 2006-08-29
forum: Desktop Environments
---

### Post by lone_marauder on 2006-08-29
I need libperlmenu-perl-4.0-4.

When I do an "reload" via synaptic, the most recent version shown is 4.0-3.  When I kick back to aptitude and do an update there, I still see the same thing.

If I manually browse my universe repository, I can see the 4.0-4 package:

[http://us.archive.ubuntu.com/ubuntu/pool/universe/libp/libperlmenu-perl/libperlmenu-perl_4.0-4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/libp/libperlmenu-perl/libperlmenu-perl_4.0-4_all.deb)

I can probably manually download it and install it via dkpg, but now I am concerned - why am I not seeing updated packages when I do an update?

---

### Post by mlind on 2006-08-29
That newer package is for Edgy. Dapper has only version 4.0-3.

---

### Post by lone_marauder on 2006-08-29
Thanks.  For future reference, how can I find that information?

---

### Post by mlind on 2006-08-29
> **lone_marauder said:**
> Thanks.  For future reference, how can I find that information?

apt-cache show *package* (dpkg -p *package* does the same, but works only  for installed packages).

apt-cache lists all available versions for this package.

---

