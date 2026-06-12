---
title: "Compiz Segfaults in differents libraries"
date: 2011-08-20
forum: Desktop Environments
---

### Post by nereid on 2011-08-20
Hello everybody,

I am a little bit fed up at the moment, as compiz has decided to segfault from time to time. Some days things work perfectly, other days I do have three or four segfaults in different libraries, resulting sometimes in a restart of compiz or sometimes in a desktop with a wallpaper but no running compiz anymore.

As far as I know, these things are all more or less related to graphic intensive work: gaming or using flash.

These are some of the segfault messages:
```
[49204.867030] compiz[14934]: segfault at 3e3b200 ip 002e3986 sp bfcfdf88 error 4 in ld-2.13.so[2d6000+1c000]
[64728.241481] compiz[16489]: segfault at c ip 00748c0e sp b7802b78 error 4 in libc-2.13.so[6dd000+15a000]
[25698.794627] compiz[1587]: segfault at 89003c24 ip 075a571e sp bffb9b94 error 6 in libnvidia-glcore.so.270.41.06[64e0000+16b5000]
[30653.893312] compiz[3793]: segfault at 4 ip 01e58186 sp bfea93b0 error 6 in libnvidia-glcore.so.270.41.06[108c000+16b5000]
[30654.252226] compiz[5057]: segfault at 61882 ip 005e2009 sp bf9b8cc8 error 4 in libstdc++.so.6.0.14[553000+df000]
[ 5965.559863] compiz[1552]: segfault at 766a8541 ip 013c4b76 sp bf8e0ec8 error 4 in libnux-core-0.9.so.0.944.4[1399000+4d000]
```

By the way, it seems, that Natty is quite segfault happy. I did not had this amount of segfaults in the older versions of Ubuntu (I had some nautilus, bamfdaemon and weather indicator segfaults too [although I did not count the ones from chromium out, as I use the daily built which could include some of those]).

---

