---
title: "Remove Gnome-desktop"
date: 2011-03-07
forum: Desktop Environments
---

### Post by impendingVOID on 2011-03-07
I installed 10.10 to play with Unity, I hated it, I've installed Kubuntu-desktop and now I want to remove ubuntu-desktop/gnome completely without having to remove all of the packaged manually.

I don't want or need the gnome packages, and updating the system is a bitch and a waste of bandwidth.

'Sudo apt-get remove ubuntu-desktop' only removed 66.7kb of packages.

Any ideas much appreciated.

Cheers,

Mark.

---

### Post by Jahid65 on 2011-03-08
```
sudo apt-get autoremove gnome*
```But it is not an ideal choice. Your system may become unusable.


or remove apps with their suggested name. i.e if you want to remove firefox, evolution, empathy together, then run this
```
sudo apt-get autoremove firefox evolution empathy
```

---

### Post by wilee-nilee on 2011-03-08
Go to playing around lower left side panel.
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

