---
title: "When to use which updater"
date: 2005-10-05
forum: Desktop Environments
---

### Post by Deekin on 2005-10-05
Hiya:

I just installed yesterday. Can someone please give a brief overview of when APT-GET, Synaptic, and er, the other one (I'm not at home now to check) is best used? I'm not sure why we have three package installers. Thanks.

---

### Post by KingBahamut on 2005-10-05
Stay with synaptic, its accessible fromt the GUI, System > Administration > Synaptic Package Manager

Thats the easiest way for you to manage your system. 

aptitude and apt-get are command line utilities and if your a fresh starter , you dont want to get acquainted with these yet. 

The KDE version of synaptic is Knaptic.

---

### Post by Deekin on 2005-10-05
[QUOTE=KingBahamut]Stay with synaptic, its accessible fromt the GUI, System > Administration > Synaptic Package Manager
Thats the easiest way for you to manage your system. 
aptitude and apt-get are command line utilities and if your a fresh starter , you dont want to get acquainted with these yet. 
The KDE version of synaptic is Knaptic.[/QUOTE]

Update-manager, thats the third one! OK, so stick with Synaptic. Will Synaptic have all the debs that apt-get would have also? I don't fear the command line, but like a nice GUI when I can get my mitts on one.

---

### Post by Corvillus on 2005-10-06
It all boils down to the fact that there's only one package management tool, apt-get. The others are actually frontends to this tool, and as a result, work identically, so it is just a matter of preference.

---

### Post by Kyral on 2005-10-06
Gotta love the heirarchy of APT.

GNOME Add/Remove ->(Here -> means is a frontend for) Synaptic -> Aptitude -> Apt -> DSelect -> DPKG. Even DPKG could be considered a frontend for source tarballs....

---

