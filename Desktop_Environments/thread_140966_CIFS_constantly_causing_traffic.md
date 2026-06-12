---
title: "CIFS constantly causing traffic"
date: 2006-03-07
forum: Desktop Environments
---

### Post by blue cube on 2006-03-07
I have a mess of mounted network drives (13)
from my win2003 server.

in my fstab I have them mounted like so:

```
//[COLOR="Red"]SERVERIP[/COLOR]/[COLOR="Red"]SHARENAME[/COLOR]     /media/[COLOR="Red"]SHARENAME[/COLOR] cifs credentials=/root/.smbcredentials,dmask=777,fmask=777       0       0
```

the question is, after I open a share, even with everything closed, no programs running anything on the remote shares, no file browsers open..

I have constant network traffic from my machine to the server...
it never stops..

its causing undue traffic. the minute I pull the cat5 plug from my system it stops, plug it back in and within seconds it starts again, from my machine to the server

does anyone have any ideas???

---

### Post by blue cube on 2006-03-07
-bump-

no one??

---

