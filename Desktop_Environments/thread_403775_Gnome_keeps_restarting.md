---
title: "Gnome keeps restarting"
date: 2007-04-07
forum: Desktop Environments
---

### Post by magictoken on 2007-04-07
Hi all. I have Edgy on Dell Dimension 9200, dual Dell monitors, Beryl, nVidia 7200 card.
It all worked fine for a month or so. I don't know what I did, but I can no longer start gdm:
it keeps restarting itself after I enter credentials into greeter app. No errors in xorg log. I tried choosing different startup Session options: "Last Session", "GNOME", "Failsafe GNOME" etc. All but the terminal produces same effect. For some reason I had this suspicion that it is somehow related to gaim - but I uninstalled it. Still same problem. Any ideas? Am I missing some log files with errors? 

Thanks a lot.

---

### Post by magictoken on 2007-04-07
Just an update: added another user, restarted gnome as this user - started just fine. So the question is - how do I identify the problem with the first user? Any help appreciated.

Cheers

---

### Post by mayonaise15 on 2007-04-07
Same problem here =(

---

### Post by magictoken on 2007-04-07
Ok, the problem is with beryl. I think I installed these new updates several days ago and they broke it.  To fix the problem: "sudo apt-get remove beryl".

---

