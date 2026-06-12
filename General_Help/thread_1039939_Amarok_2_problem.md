---
title: "Amarok 2 problem"
date: 2009-01-15
forum: General Help
---

### Post by thestig_992 on 2009-01-15
A while ago i made a post about fixing amarok 2 when it wasnt displaying properly, but i could get it fixed so i sort of left it. Now im trying again, and i have this error message that just appeared after reinstalling amarok 2.
```

Amarok could not find any collection plugins. Amarok is now updating the KDE configuration database. Please wait a couple of minutes, then restart Amarok.
If this does not help, it is likely that Amarok is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca4 --noincremental
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.
```

i can understand every step but the first one; i really have no idea what directory the amarok source code is in...

Just for reference, this is the old thread i made, though i dont think it will be much help...[http://ubuntuforums.org/showthread.php?t=1013426](http://ubuntuforums.org/showthread.php?t=1013426)

---

### Post by thestig_992 on 2009-01-15
sorry, worked it out now XD

---

