---
title: "nautilus keeps segfaulting when trying to connect to samba share."
date: 2009-07-25
forum: Desktop Environments
---

### Post by thedlw on 2009-07-25
ok well i keep getting this.

[11425.093139] nautilus[3155]: segfault at b7a05228 ip b78cf47d sp bfd560c0 error 7 in libglib-2.0.so.0.2103.0[b7875000+d8000]
[11692.254354] nautilus[7778]: segfault at 73756c69 ip b781e47b sp bfba4210 error 4 in libglib-2.0.so.0.2103.0[b77c4000+d8000]
[11887.704992] nautilus[8113]: segfault at b795a228 ip b782447d sp bf9aa150 error 7 in libglib-2.0.so.0.2103.0[b77ca000+d8000]
[11999.082813] nautilus[8198]: segfault at 73756c69 ip b785d47b sp bfce4b40 error 4 in libglib-2.0.so.0.2103.0[b7803000+d8000]
[12452.509784] nautilus[8483]: segfault at 2 ip b787147b sp bf8f8f50 error 4 in libglib-2.0.so.0.2103.0[b7817000+d8000]

i'm trying to connect to my samba share on my ubuntu server box
i've already tried reinstalling nautlius and libglib2

Also nautilus works just fine locally its only when trying to connect remotely.

---

