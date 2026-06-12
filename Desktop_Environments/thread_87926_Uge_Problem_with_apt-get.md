---
title: "Uge Problem with apt-get"
date: 2005-11-09
forum: Desktop Environments
---

### Post by kapa_des on 2005-11-09
When ever I type an apt-get command I get this:
root@kapanet:/home/kapaciu # apt-get remove opendchub
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  amarok: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not going to be installed
          Depends: libsqlite3-0 (>= 3.2.1) but it is not going to be installed
          Depends: libtag1c2 (>= 1.3.1) but it is not going to be installed
          Depends: libtunepimp2c2 (>= 0.3.0) but it is not going to be installed  amarok-gstreamer: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not going to be installed
                    Depends: libgstreamer0.8-0 (>= 0.8.11) but 0.8.9-1ubuntu4 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@kapanet:/home/kapaciu # apt-get remove amarok

And if I continue with apt-get -f install it will install amarok that needs KDE and it will delet my Gnome Desktop .... what should I do?

---

### Post by kapa_des on 2005-11-09
plz help ...I can't remove or download anything :( :( :(

---

