---
title: "Error: Cannot Find Name for group ID XXXXXXXXX"
date: 2008-09-10
forum: Desktop Environments
---

### Post by farles on 2008-09-10
I have winbind authenticaion setup on my LTSP server.  
I added my machine to the domain using likewise. and I 
I have added the below so I don't have to always type Domain\Username:
winbind use default domain = yes
to
/etc/samba/lwiauthd.conf
But, now I get "id: cannot find name for group id 998245463"
when I try to chroot

Any help would be appreciated.

---

### Post by farles on 2008-09-12
Anyone have any ideas?  If I remove: "winbind use default domain = yes" from "/etc/samba/lwiauthd.conf" it works, but my users have to enter Domain\Username to login.  
I would really appreciate any input. Thanks.

---

