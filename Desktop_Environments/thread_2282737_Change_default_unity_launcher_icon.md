---
title: "Change default unity launcher icon"
date: 2015-06-16
forum: Desktop Environments
---

### Post by orglce on 2015-06-16
Hello, 

I was wondering if I could somehow change the default Ubuntu unity launcher icon.

Thanks in advance.

[IMG]http://shrani.si/f/5/ub/1oj5fsex/screenshot-from-2015-06-.png[/IMG]

---

### Post by deadflowr on 2015-06-16
It's in /usr/share/unity/icons.
It's the launcher_bfb.png file.
Simply copy whatever image you want over that.
Something like:
```
sudo cp /path/to/new/image /usr/share/unity/icons/launcher_bfb.png
```

Note that whenever an update for unity comes it'll overwrite these files and thus replace your replaced icon.
It should also be of note that the location has changed between various versions of Ubuntu, so while it currently is in the icons folder, it has been in a different folder before.
(In Ubuntu 12.04 it is in /usr/share/unity/5 )

I would also suggest try making the image the same size as the existing icon, which is (for me at least) 128x128px

---

### Post by coffeecat on 2015-06-16
*Thread moved to **Desktop Environments**.*

---

### Post by orglce on 2015-06-17
Thanks! :D

---

