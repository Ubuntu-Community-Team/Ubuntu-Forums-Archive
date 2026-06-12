---
title: "launcher icon with question mark (Ubuntu 14.04)"
date: 2014-06-25
forum: Desktop Environments
---

### Post by a_m on 2014-06-25
Hallo,
I am on Ubuntu 14.04 and I have created a permanent launcher icon for an application (precisely, /opt/anaconda/bin/spyder) by right clicking on it and locking it to the launcher. However, the icon has an ugly question mark and I find no way to change it. Editing these files was no help

$ locate spyder.desktop
/opt/anaconda/pkgs/spyder-2.3.0rc1-py27_0/share/applications/spyder.desktop
/opt/anaconda/share/applications/spyder.desktop
/usr/share/app-install/desktop/spyder:spyder.desktop
/usr/share/applications/spyder.desktop

so I guess I am looking in the wrong place. How to change this icon? Thanks!

---

### Post by cheflo on 2014-09-05
Hi,
Did you ever solve this? I am having the same issue.

---

### Post by cheflo on 2014-09-05
Figured it out. Copy any launcher from /usr/share/applications/. Right click and go to properties, change the command line to
```
~/anaconda/bin/spyder
``` (or wherever you installed your anaconda).
Change the rest of the info and the icon accordingly. Move the launcher ~/.local/share/applications/, and it should now pop up in your application menu. There might be other places where you can put it as well, but this is what worked for me.

---

