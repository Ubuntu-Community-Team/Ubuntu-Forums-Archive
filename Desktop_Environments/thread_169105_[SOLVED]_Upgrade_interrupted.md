---
title: "[SOLVED] Upgrade interrupted"
date: 2006-05-01
forum: Desktop Environments
---

### Post by Ulongu on 2006-05-01
A short power outage occured in the middle of an upgrade.  When I try to re-do apt-get upgrade I get this

rich@ubuntu:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
rich@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0034' near line 1:
 newline in field name `/.'

What should I do now?

---

### Post by Sef on 2006-05-02
> you must manually run 'dpkg --configure -a'

This tells you what to do.  Opern the terminal (Applications > Accessories > Terminal)

then 

dpkg -configure -a

if it doesn't run like that, then add sudo at the beginning.

sudo dpkg -configure -a

---

### Post by Ulongu on 2006-05-02
I did that and this happened

rich@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0034' near line 1:
newline in field name `/.'

---

### Post by Ulongu on 2006-05-02
This is what /var/lib/dpkg/updates/0034 looks like

/.
/usr
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/gedit
/usr/share/doc
/usr/share/doc/gedit
/usr/share/doc/gedit/changelog.Debian.gz
/usr/share/doc/gedit/TODO
/usr/share/doc/gedit/BUGS
/usr/share/doc/gedit/AUTHORS
/usr/share/doc/gedit/copyright
/usr/share/doc/gedit/changelog.gz
/usr/share/doc/gedit/NEWS.gz
/usr/share/doc/gedit/README.gz
/usr/share/menu
/usr/share/menu/gedit
/usr/share/gconf
/usr/share/gconf/schemas
/usr/share/gconf/schemas/gedit.schemas
/usr/bin
/usr/bin/gedit
/usr/lib
/usr/lib/gedit-2
/usr/lib/gedit-2/plugins
/usr/lib/gedit-2/plugins/changecase.gedit-plugin
/usr/lib/gedit-2/plugins/docinfo.gedit-plugin
/usr/lib/gedit-2/plugins/externaltools.gedit-plugin
/usr/lib/gedit-2/plugins/indent.gedit-plugin
/usr/lib/gedit-2/plugins/modelines.gedit-plugin
/usr/lib/gedit-2/plugins

---

### Post by Chris03 on 2006-05-03
I think the problem could be with the . at the end, since only a / is the sign for the root location, no period. Not sure how it got there, but it could be due to the power outage. Terminal command:

sudo gedit /var/lib/dpkg/updates/0034

Then, remove the . and save. Try again and see if it works :)

---

### Post by Ulongu on 2006-05-03
Thanks for the reply, but I already gave up and did a re-install.

---

### Post by Chris03 on 2006-05-04
Reinstalling Ubuntu is fun! Bringing the system up to date takes less than 5 minutes, and no restarts! :)

---

### Post by skralljt on 2007-12-24
I had something similar happen, I opened the file /var/lib/dpkg/0026 or whatever, fiddled around trying to remove or add characters that looked out of place a few times and saved and tried to sudo apt-get update but nothing worked.   Finally I did sudo rm /var/lib/dpkg/0026 and then did apt-get update and upgrade and it worked.   Just delete the file and update the whole stupid thing.

---

