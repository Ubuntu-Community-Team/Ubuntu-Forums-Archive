---
title: "AWN Package and dependencies"
date: 2009-03-15
forum: General Help
---

### Post by masterchief1995 on 2009-03-15
I have a desktop running Ubuntu 8.04 and I wanted to get AWN for it but I don't have a direct internet connection. I can download packages, transfer them via USB and then install. Could anyone give me a list of packages and dependencies for it.:D

---

### Post by run1206 on 2009-03-15
> **masterchief1995 said:**
> I have a desktop running Ubuntu 8.04 and I wanted to get AWN for it but I don't have a direct internet connection. I can download packages, transfer them via USB and then install. Could anyone give me a list of packages and dependencies for it.:D

this is what i get from terminal...
```
run1206@run1206-laptop:~$ sudo apt-get install awn-(pressed tab for others...)
awn-applets-c-core         awn-applets-python-extras
awn-applets-c-extras       awn-manager
awn-applets-python-core 

```

just a heads up that i'm using Intrepid, don't know if they'll change the repositories...

here's the extras...
```

run1206@run1206-laptop:~$ sudo apt-get install awn-manager awn-applets-c-core awn-applets-c-extras awn-applets-python-core awn-applets-python-extras 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  avant-window-navigator avant-window-navigator-data libawn-extras0 libawn0
  python-alsaaudio python-awn python-awn-extras python-awnlib
The following NEW packages will be installed:
  avant-window-navigator avant-window-navigator-data awn-applets-c-core
  awn-applets-c-extras awn-applets-python-core awn-applets-python-extras
  awn-manager libawn-extras0 libawn0 python-alsaaudio python-awn
  python-awn-extras python-awnlib
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 2262kB of archives.
After this operation, 11.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y

```

---

### Post by masterchief1995 on 2009-03-15
thanks so much!:D

---

