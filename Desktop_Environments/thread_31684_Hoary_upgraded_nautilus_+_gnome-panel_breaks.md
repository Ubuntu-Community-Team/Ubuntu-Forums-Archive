---
title: "Hoary upgraded nautilus + gnome-panel breaks"
date: 2005-05-04
forum: Desktop Environments
---

### Post by prem_mallappa on 2005-05-04
Hi all,
Just installed ubuntu hoary

apt/sources.list

deb [http://cnt.archive.ubuntu.com/ubuntu](http://cnt.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) hoary universe
----------------------------------------------------------------------------------------------

gnome-panel and nautilus starts and closes again and again. doesn't allow me to do anything.
please let me know the if the latest debs to ubuntu are broken

---

### Post by Juergen on 2005-05-04
I don't know about your mirrors, but my upgrade went nearly without problems.

Nearly because I had to manually (de-)install 2 packages that stopped the process.
Maybe you have the same and your update isn't complete?

What happens if you log in to a console and type
```
sudo apt-get -f install
```?

---

### Post by prem_mallappa on 2005-05-04
apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.


the two not upgraded is apt and apt-utils, i need the debian stuff here since my proxy blocks *.bz2 and somehow allows *.gz so debian apt stuff downloads Packages.gz but hoary->apt downloads Packages.bz2.

Does anybody (ubuntu users,developers,lovers.....) has answer for this.

---

