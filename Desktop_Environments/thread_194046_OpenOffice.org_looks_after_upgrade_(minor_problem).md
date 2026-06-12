---
title: "OpenOffice.org looks after upgrade (minor problem)"
date: 2006-06-10
forum: Desktop Environments
---

### Post by rskovacs on 2006-06-10
OK, so I upgraded from Breezy to Dapper via apt-get.  OpenOffice got totally uninstalled during the dist-upgrade (I guess because I had installed 2.0 from a repository which I removed from sources.list pre-upgrade?) and then had to reinstall it after the Dapper upgrade completed.  Now strangely enough, the OpenOffice menus will not assume the fonts/colors of the current GNOME theme like they used to.  It's not a huge deal, it just looks bad.  Anyone have any idea what's up?

---

### Post by stlutz on 2006-06-11
Have you installed openoffice.org2-gnome?

---

### Post by rskovacs on 2006-06-13
Well, I just did, and that fixed everything.  Thanks!

---

