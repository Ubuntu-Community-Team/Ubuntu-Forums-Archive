---
title: "Could not display &quot;network:&quot;"
date: 2012-04-09
forum: Desktop Environments
---

### Post by Nickolai_Leschov on 2012-04-09
Something has broken in my Nautilus. When I select "Places" -> Network from dropdown menu, it says:
> Could not display "network:".
The same goes for "Places" -> "Computer"


[LIST=1]
[*]How do I fix that?
[*]How else can I browse network?
[/LIST]
Ubuntu 9.04 i386, Gnome 2.26.1

---

### Post by Morbius1 on 2012-04-09
It really sounds like you are missing some packages:
```
sudo apt-get install gvfs-backends
``````
sudo apt-get install gvfs-fuse
```Not sure how that could have happened all of a sudden though.

---

