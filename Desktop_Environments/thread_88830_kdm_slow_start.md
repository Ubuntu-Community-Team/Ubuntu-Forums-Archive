---
title: "kdm slow start"
date: 2005-11-11
forum: Desktop Environments
---

### Post by whittycat on 2005-11-11
Kubuntu 5.04 - kdm takes ages to load; the time from loading the OS to seeing the kdm login
screen is 4m55s. The file /var/log/kdm.log has lots of debug entries in it. Where do these come
from and how can I switch them off?

Oh and a bug report (the 'new' way of reporting bugs gives me 'page not found'). . If I install tcsh 
and change /etc/passwd to set the login shell to tcsh kdm refuses to go to KDE but just gives me 
the login screen again. 

Tony Sumner

---

### Post by whittycat on 2005-11-11
I upgraded to 5.10 and it invited me to install the maintainer's version of kdm, which
I did and the slow start problem has gone away. I think the trouble may have related
to my attempt to use fvwm; I'll get back to that but cautiously. Meanwhile I shall 
enjoy the badgery.

whittycat

---

