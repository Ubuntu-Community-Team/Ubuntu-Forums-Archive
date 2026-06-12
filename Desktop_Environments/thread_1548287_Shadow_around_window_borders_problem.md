---
title: "Shadow around window borders problem"
date: 2010-08-08
forum: Desktop Environments
---

### Post by not1 on 2010-08-08
Hi guys.

I downloaded Cairo dock yesterday and it meddled with some configurations. Specifically I think it turned on compiz and put some shadow around my windows.

I didn't like that or the software itself so I uninstalled it. I used the metacity -replace function and I also have my visual effects set to zero.

I still have a terrible looking shadow :( :(

Why and how can I disable it?

---

### Post by stinkeye on 2010-08-08
Have a look in gconf-editor > /apps/metacity/general/compositing_manager
and see if disabling or enabling compositing_manager changes it back to how you like it.
In a default install I think the compositing feature for Metacity is disabled.

---

### Post by not1 on 2010-08-08
Yeah it worked when I disabled :)

Thanks a bunch stinkeye :D

---

