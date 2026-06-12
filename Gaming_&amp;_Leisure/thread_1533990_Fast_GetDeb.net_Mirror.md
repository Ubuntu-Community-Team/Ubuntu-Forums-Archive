---
title: "Fast GetDeb.net Mirror"
date: 2010-07-18
forum: Gaming &amp; Leisure
---

### Post by kiplingw on 2010-07-18
I've setup a high performance, reliable, mirror for getdeb.net, courtesy of the Avaneya project.

```
deb http://getdeb.avaneya.com/ubuntu lucid-getdeb apps
deb http://getdeb.avaneya.com/ubuntu lucid-getdeb games
```

---

### Post by Wise Ferret on 2010-07-29
Hi Kiplingw,

When I try to use your repository I can update fine, but upon trying to upgrade packages I get:


Err [http://getdeb.avaneya.com/ubuntu/](http://getdeb.avaneya.com/ubuntu/) lucid-getdeb/games violetland 0.3.0-1~getdeb2
403 Forbidden
Err [http://getdeb.avaneya.com/ubuntu/](http://getdeb.avaneya.com/ubuntu/) lucid-getdeb/games violetland-data 0.3.0-1~getdeb2
403 Forbidden
Failed to fetch [http://getdeb.avaneya.com/ubuntu/pool/games/v/violetland/violetland_0.3.0-1~getdeb2_amd64.deb](http://getdeb.avaneya.com/ubuntu/pool/games/v/violetland/violetland_0.3.0-1~getdeb2_amd64.deb) 403 Forbidden
Failed to fetch [http://getdeb.avaneya.com/ubuntu/pool/games/v/violetland/violetland-data_0.3.0-1~getdeb2_all.deb](http://getdeb.avaneya.com/ubuntu/pool/games/v/violetland/violetland-data_0.3.0-1~getdeb2_all.deb) 403 Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by _h_ on 2010-07-29
[yea im dumb]

---

### Post by kiplingw on 2010-07-29
Wise, please accept my apologies. It was trivial to fix at my end. Should be up and running now. Thanks for pointing that out.

---

### Post by kiplingw on 2010-11-12
I should have mentioned this earlier, but forgot. The mirror now has Maverick packages.

```

deb http://getdeb.avaneya.com/ubuntu maverick-getdeb apps
deb http://getdeb.avaneya.com/ubuntu maverick-getdeb games

```

---

