---
title: "Desktop environment switch"
date: 2008-03-02
forum: Desktop Environments
---

### Post by Skald on 2008-03-02
Hello everyone
If I have installed Ubuntu and later find out that I want KDE instead, will I be able to switch it somehow like in fedora or do I have to download Kubuntu and reinstall the whole installation?

---

### Post by scragar on 2008-03-02
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

---

### Post by lary on 2008-03-09
So, i have Ubuntu 7.10(amd64). I installed kubuntu-desktop from synaptic and kde4-core.When choose kde session everything is fine but when i choose kde4 all i get is a blank screen.Any help with kde4?Thanks!

---

### Post by scragar on 2008-03-09
you will need to add the KDE4 repository:
```
gksudo gedit /etc/apt/sources.list
```and at the end add:```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu gutsy main
```
save and close, then run ```
sudo apt-get update
```to update the list and finaly upgrade to a working version: ```
sudo apt-get install kde4-core
```


oh, and you will need to disable compiz(the desktop effects) before you can run KDE4 for some reason, so check that as well.

---

