---
title: "Can't use kwrite in konqueror root"
date: 2005-04-12
forum: Desktop Environments
---

### Post by bigblop on 2005-04-12
If I in a shell type:

kdesu 'konqueror --profile Myview'

I can then edit ie. XF86Config-4 and save it with kwrite through konqueror.

But when I try to do the exact same thing after closing konqueror I get this
error when I try to open XF86Config-4

KDEInit could not launch 'kwrite'


For some reason it only works correct the first time, the second time I get
this error...is it a bug?

---

### Post by Xian on 2005-04-12
You might try just a more direct 'kdesu konqueror' and see if that will work, or you can open kwrite directoy as 'kdesu kwrite'. I've gotten those messages at times in other distros and they seem to be inconsistent and temporary.

---

