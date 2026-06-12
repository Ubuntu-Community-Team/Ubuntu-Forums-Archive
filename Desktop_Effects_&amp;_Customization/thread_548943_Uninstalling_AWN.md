---
title: "Uninstalling AWN"
date: 2007-09-11
forum: Desktop Effects &amp; Customization
---

### Post by jeffthespasm on 2007-09-11
I've had Avant Window Navigator installed for some time now, and I still want to continue using it. However, I want to COMPLETELY remove it from my system and start over from scratch. I originally built it from SVN source and have since applied patches which did not work, etc. Now I'm having some problems with it and I'd much rather remove it and reinstall it clean so the patches would work.

When I try to 'sudo make uninstall' in the svn directory, I get this message:

```
cd . && /bin/bash /home/jeff/svn/avant-window-navigator/missing --run aclocal-1.10 
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
/usr/share/aclocal/oaf.m4:4:   run info '(automake)Extending aclocal'
/usr/share/aclocal/oaf.m4:4:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
configure.in:65: error: `applets/stack/Makefile' is already registered with AC_CONFIG_FILES.
../../lib/autoconf/status.m4:300: AC_CONFIG_FILES is expanded from...
configure.in:65: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal-1.10: autom4te failed with exit status: 1
make: *** [aclocal.m4] Error 1
```

Any help would be greatly appreciated!

Thanks,
Jeff

---

