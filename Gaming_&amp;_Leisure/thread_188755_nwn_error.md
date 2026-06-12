---
title: "nwn error"
date: 2006-06-04
forum: Gaming &amp; Leisure
---

### Post by PriceChild on 2006-06-04
Hi, i've recently done a fresh install of my system, copying over several things including the /usr/local/games/ dir.

However, i'm getting the following error:
```

[CENTER]
 pricechild@thebeast:/usr/local/games/neverwinter$ nonXgl nwn
non-network local connections being added to access control list
./nwmain: error while loading shared libraries: libmss.so.6: cannot open shared object file: No such file or directory[/CENTER]

```
 Please help, Pricey

P.s. the nonXgl command is used to help 3dacceleration work as i'm running xgl/compiz - all other games work fine.

---

### Post by seth0x2b on 2006-06-04
try copying the <nwn directory>/miles folder contents to /usr/lib/

Cheers
[EDIT] Don't forget to run "ldconfig" after this

Also, check this link :) [http://nwn.bioware.com/forums/viewtopic.html?topic=468091&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=468091&forum=72)

---

