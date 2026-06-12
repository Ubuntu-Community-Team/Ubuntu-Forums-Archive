---
title: "ubuntu-desktop No Longer Installs OpenOffice.org"
date: 2010-11-30
forum: Desktop Environments
---

### Post by rykel on 2010-11-30
Hi, in Maverick, **sudo apt-get install ubuntu-desktop** no longer installs OpenOffice.org... (date - 30 Nov 2010)

Do you know if OOo has been quietly removed as the default Ubuntu office suite?

---

### Post by a-user on 2010-11-30
no, it is still the default office suit. i had it installed by default when installing from cd. maybe only the dependency to ubuntu-desktop metapackage has been removed.

---

### Post by rykel on 2010-12-01
I removed ubuntu-desktop when I uninstalled transmission-gtk, and upon reinstalling ubuntu-desktop, it requested me to reinstall OOo as well. So the problem is that ubuntu-desktop no longer pulls in OOo when it (ubuntu-desktop) already exists on the system, but it will when it is not.

---

### Post by akand074 on 2010-12-01
That's interesting but I guess it's only one extra command to get open office installed too. So it's not a big deal.

---

