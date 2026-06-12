---
title: "devolo lan cockpit"
date: 2013-08-29
forum: Desktop Environments
---

### Post by Ofloo on 2013-08-29
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
```


Package devolo-dlan-cockpit version 4.1.3-0 and 4.1.2-0 had this also, don't show the when the client is activated it doesn't show a window I can see it really fast flashing by but then it becomes invissible.

Two versions of xubuntu ago it worked just fine, it's been disfunctional for a while now, i think the problem however is with adobe air, anyways anyone any idea how to fix this.

---

### Post by thomi_ch on 2013-10-28
hi

i also have this problem. I run manually /opt/devolo/dlancockpit/bin/dlancockpit-run.sh and i only see the task-bar entry, but no program window.

Any hints are welcome

Regards
thomi

---

### Post by thomas.smets on 2013-11-11
The crash here is pretty obvious ... on an Ubuntu 12.04 LTS
I will update with the stack trace as soon as I can get one (I already reported this once ... and now it seems it is not being proposed during this session).

\T,

---

### Post by Philippe_Kerlirzin on 2014-01-18
Hello,
I have the same problem on Ubuntu 12.04. 
I tried : sudo /opt/devolo/dlancockpit/bin/dlancockpit in a terminal.
It asked me to accept terms for installing AdobeAir and then I had this message in the terminal : Unknown desktop manager, only Gnome and KDE are supported.
I think this is the answer why it doesn't work.

---

