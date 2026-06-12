---
title: "Problem with new Amarok package"
date: 2006-01-16
forum: General Help
---

### Post by jrattner on 2006-01-16
After performing a system update from "Update Manager", the upgraded version of Amarok was installed.  When I went to launch it, the following error occurs:

amaroK could not find any sound-engine plugins. amaroK is now updating the KDE configuration database. Please wait a couple of minutes, then restart amaroK.
If this does not help, it is likely that amaroK is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.

Has anyone had a similar problem?

---

