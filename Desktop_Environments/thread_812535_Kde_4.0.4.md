---
title: "Kde 4.0.4"
date: 2008-05-30
forum: Desktop Environments
---

### Post by open_coder on 2008-05-30
I followed the instructions on Kubuntu's site for installing KDE 4.0.4 but when I go to the check the version number, I am still running 4.0.3. Does anybody else have this problem? How can I fix it?

Alex

---

### Post by p_quarles on 2008-05-30
It may be that the new version is in a separate directory, and is not the default KDE 4 suite. Try running:
```
which kded
```
and post the results here.

---

### Post by geoffmacartney on 2008-05-31
I'm still stuck on 3.5.9, according to "About KDE" , plus :

$ which kded
/usr/bin/kded
$ kded --version
Qt: 3.3.8b
KDE: 3.5.9
KDE Daemon: $Id: kded.cpp 711061 2007-09-11 09:42:51Z tpatzig $

But dpkg tells me I have a bunch of KDE 4.3 packages, as far as I can tell:

$ dpkg-query -l '*kde*' | grep 'ii.*4:3' | awk '{print $2, $3}'
kde-icons-mono 4:3.5.9-0ubuntu1
kdeadmin-kfile-plugins 4:3.5.9-0ubuntu5
kdebase-bin 4:3.5.9-0ubuntu7.2
kdebase-bin-kde3 4:3.5.9-0ubuntu7.2
kdebase-data 4:3.5.9-0ubuntu7.2
kdebase-kio-plugins 4:3.5.9-0ubuntu7.2
kdegraphics-kfile-plugins 4:3.5.9-0ubuntu1
kdelibs-data 4:3.5.9-0ubuntu7.1
kdelibs4c2a 4:3.5.9-0ubuntu7.1
kdemultimedia-kfile-plugins 4:3.5.9-0ubuntu2
kdemultimedia-kio-plugins 4:3.5.9-0ubuntu2
kdenetwork-filesharing 4:3.5.9-0ubuntu1
kdenetwork-kfile-plugins 4:3.5.9-0ubuntu1
kdepasswd 4:3.5.9-0ubuntu7.2
kdepim-kio-plugins 4:3.5.9-0ubuntu3
kdepim-kresources 4:3.5.9-0ubuntu3
kdepim-wizards 4:3.5.9-0ubuntu3
kdeprint 4:3.5.9-0ubuntu7.2
kdesktop 4:3.5.9-0ubuntu7.2
libkdepim1a 4:3.5.9-0ubuntu3


How can I switch to KDE 4?

---

