---
title: "Wicd and the Dell mini 9"
date: 2009-03-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Arndtwe on 2009-03-14
I have recently become interested in a network manager called Wicd. I have followed the Ubuntu installation instruction [HERE]("http://wicd.net/download.php") and it will not show up in synaptic... Any help would be appreciated. 

P.S. I did download the .deb package and opened it in GDebi Package Installer, and it would not let me install the packed due to the error: Conflicts with installed package 'network-manager'.

---

### Post by ugm6hr on 2009-03-14
You have to remove NM first.

```
sudo apt-get remove network-manager
```

Remember networking won't work once you've done this.

To download NM to your HD, just in case first:
```
sudo apt-get install --reinstall -d network-manager network-manager-gnome
```

---

### Post by phantom3113 on 2009-03-14
Before wicd shows up in synaptic, you'll need to add it to the repositories which should be this: deb [http://apt.wicd.net](http://apt.wicd.net) (this is under Administration>>Software Sources>>Third Party Sources (or software)>>Add) Once you reload, do a search for "wicd" (not quick search, regular search) and it should be there. Getting it through synaptic downloads it, uninstalls NM, and then installs wicd in a few steps on it's own. If you already have the .deb package, you might as well try what ugm6hr offered first though :) Just a note though: having wicd in the repositories will make synaptic look for any updates that may eventually come available.

---

