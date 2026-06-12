---
title: "where's my KDE4?"
date: 2008-06-01
forum: Desktop Environments
---

### Post by geoffmacartney on 2008-06-01
Although I've upgraded to 8.04, I'm still stuck on KDE 3.5.9, according to "About KDE" , plus :

$ which kded
/usr/bin/kded
$ kded --version
Qt: 3.3.8b
KDE: 3.5.9
KDE Daemon: $Id: kded.cpp 711061 2007-09-11 09:42:51Z tpatzig $

But dpkg tells me I have a bunch of KDE 4 packages, as far as I can tell:

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


I thought upgrading to 8.04 would put me on KDE 4. How can I switch to it?

cheers
Geoff

---

### Post by benerivo on 2008-06-01
Install the kde4-core package```
sudo apt-get install kde4-core
```You will then be able to log in to either a kde3 or kde4 desktop environment.

---

### Post by Xiong Chiamiov on 2008-06-01
Aside from that, Kubuntu Hardy was released in two different versions: the supported 3.5 and the unsupported 4.

---

### Post by geoffmacartney on 2008-06-01
That's it, having installed the packages as above, I'm now up and going with KDE4, which looks really cool, I might add...

many thanks!

Geoff

---

