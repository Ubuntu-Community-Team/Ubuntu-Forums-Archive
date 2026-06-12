---
title: "Conky pre install errors"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Family_Guy on 2006-06-29
I'm following the guide here.

[http://ubuntuforums.org/showthread.php?t=139262](http://ubuntuforums.org/showthread.php?t=139262)

When I do the following line...

sudo apt-get install linux-headers-`uname -r` checkinstall build-essential libdbus-1-dev libdbus-glib-1-dev libxext-dev

I get this...

```
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  checkinstall: Depends: installwatch (> 0.6) but it is not going to be installed
  conky: Depends: libc6 (>= 2.3.6-6) but 2.3.5-1ubuntu12.5.10.1 is to be installed
         Depends: libfreetype6 (>= 2.2) but 2.1.7-2.4ubuntu1.1 is to be installed
         Depends: libglib2.0-0 (>= 2.10.0) but 2.8.3-0ubuntu1 is to be installed  libdbus-glib-1-dev: Depends: libglib2.0-dev but it is not going to be installed
  linux-headers-2.6.12-10-386: Depends: linux-headers-2.6.12-10 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

