---
title: "Disable update-manager"
date: 2009-05-24
forum: Desktop Environments
---

### Post by leandromartinez98 on 2009-05-24
Hello,

I want to fully disable the update manager in my
mom´s netbook. That´s because I had to do some tweaking
in order to get it fully functioning and I don´t 
want updates to breake what was done. I don´t want
her to be bothered by update messages of any kind.

I tried to disable automatic updates, but now the
update-manager pops up and says that she need to
manually check for updates. 

Basically, I would like the system to only think about
updates when I do it manually.

Is there some way to fully disable the update-manager
so it does not give any message unless requested?

Thanks.

---

### Post by ckonestroh on 2009-05-24
Simple,


Go into Administration > Update Manger > settings > select tab updates > Automatic updates unclick search for updates this should do it....


later....

chris

---

### Post by x33a on 2009-05-24
system -> preferences -> startup applications.

uncheck update notifier.

though, i would suggest you don't disable the updates all together, because they fix a lot of bugs and security holes. when updates do show up, just uncheck the ones which are likely to break your tweaks.

---

### Post by ddrichardson on 2009-05-24
Administration > Update Manger > Settings... > Updates

Choosing just the security updates would seem a sensible compromise.  I administer a number of netbooks and their small hard drives make them easy to create disc images, then when someone borks their installation I can restore it.  A live system on USB using partimage is all you need, then you can get it up and running quickly in the event of failure without a lot of tweaking.

---

### Post by leandromartinez98 on 2009-05-24
> **ckonestroh said:**
> Simple,


Go into Administration > Update Manger > settings > select tab updates > Automatic updates unclick search for updates this should do it....


later....

chris

That results in the the update manager popping up to warn me that
I need to manually check for updates.

---

### Post by leandromartinez98 on 2009-05-24
> **x33a said:**
> system -> preferences -> startup applications.

uncheck update notifier.

though, i would suggest you don't disable the updates all together, because they fix a lot of bugs and security holes. when updates do show up, just uncheck the ones which are likely to break your tweaks.

I will try that, probably it will do the trick. I have unchecked all
kinds updates in the update manager and it seems to have worked
as well, although I think I prefer your solution.

Concerning the updates, yes, that it mostly what I do, I just don't
want her to be bothered about update notifications, because she 
has no idea of what each package is.

---

