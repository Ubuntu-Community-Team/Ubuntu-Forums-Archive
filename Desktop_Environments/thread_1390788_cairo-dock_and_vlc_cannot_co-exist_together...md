---
title: "cairo-dock and vlc cannot co-exist together.."
date: 2010-01-26
forum: Desktop Environments
---

### Post by rahilm on 2010-01-26
let me get to the point,
i install vlc, it runs fine, plays fine. then i install cairo-dock which also runs fine. but now, every time i open vlc , it shuts down without playing. I don't know it is because of cairo-dock so i re-install vlc. Same problem.
then i log in in a guest session. Miiracle!!! vlc is working fine. then i log back in my account. vlc is still not working. so i guess i messed up some configuration files. I log back in guest session and start cairo-dock just like that. then suddenly vlc stops working...
it seems cairo-dock has messed up with some configuration files i don't know of, and it does not get normal even if i remove cairo-dock. What should i do??????????

---

### Post by rahilm on 2010-01-26
i answered first!!
i found this:
[http://www.mail-archive.com/cairo-dock-team@lists.launchpad.net/msg00033.html](http://www.mail-archive.com/cairo-dock-team@lists.launchpad.net/msg00033.html)
and this
[https://bugs.launchpad.net/cairo-dock-core/+bug/416294](https://bugs.launchpad.net/cairo-dock-core/+bug/416294)
and this of course:
[http://www.google.co.in/#hl=en&safe=off&q=cairo+dock+and+vlc&meta=&aq=f&oq=cairo+dock+and+vlc&fp=f939f4a34379d242](http://www.google.co.in/#hl=en&safe=off&q=cairo+dock+and+vlc&meta=&aq=f&oq=cairo+dock+and+vlc&fp=f939f4a34379d242)



i'll be reading for a solution

---

### Post by rahilm on 2010-01-26
it seems i have to install vlc 1.0.4.. the repositories have 1.0.2 and the ppa on the site has 1.0.3

---

### Post by rahuroon on 2010-02-20
use vlc opengl video mode...it will work fine.

---

