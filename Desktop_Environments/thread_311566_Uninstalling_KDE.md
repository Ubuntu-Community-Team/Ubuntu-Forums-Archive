---
title: "Uninstalling KDE"
date: 2006-12-03
forum: Desktop Environments
---

### Post by alican timur on 2006-12-03
I had been using Gnome for a while, and i also installed KDE, and now i want to completely get rid of KDE. I uninstalled all the kde packages from synaptic, but it's still there.

---

### Post by aysiu on 2006-12-03
Synaptic is a graphical frontend for *apt-get*, which--as of Dapper--does not have the ability to remove unused dependencies along with an application (this has changed for Edgy). Read more about that here:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

In the meantime, you can probably force a removal of KDE with this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

