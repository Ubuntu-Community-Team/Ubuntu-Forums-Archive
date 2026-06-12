---
title: "help reneming &quot;MSHOME&quot; TO &quot;WORKGROUP&quot;"
date: 2006-02-18
forum: Desktop Environments
---

### Post by kelloggsx on 2006-02-18
I am trying network my ubuntu box with my win2k server.

First thing i notice is that by default ubuntu box is member of "MSHOME" while all my  M$ computers are member of "WORKGROUP"

what do i have to do to make rename ubuntu box to joing the "WORKGROUP" network.

thanks..

ps.. havent installed samba or anything else, but i figure this should be the starting point.

---

### Post by knalle on 2006-02-18
edit **/etc/samba/smb.conf**, replace MSHOME with WORKGROUP

then run from terminal:

**/etc/init.d/samba restart**

---

### Post by kelloggsx on 2006-02-18
[QUOTE=knalle]edit **/etc/samba/smb.conf**, replace MSHOME with WORKGROUP

then run from terminal:

**/etc/init.d/samba restart**[/QUOTE]


work like a champ! now to issue # 3

---

