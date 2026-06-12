---
title: "Gnome on Ubuntu server"
date: 2008-06-27
forum: Desktop Environments
---

### Post by Malfet on 2008-06-27
I've install Ubuntu Server 8.04 and would like to have GNOME enviroment like in desdctop version. When I typed 
> apt-get install ubuntu-desktop 
I got message "No such package could be found (or something similar)", but both universe and multiverse deb are active. I've checked sources.list and run > sudo apt-get update aferwards.
Does anyone has a clues what I missed?
PS gdm has been installed in the same way (apt-get install gdm) without any problems.

---

### Post by Rocket2DMn on 2008-06-27
That metapackage is available in the main repository, so I'm not sure what your problem is.  You can try switching mirrors in case the one you are using is incomplete or not up to date.  Also, try using aptitude since this keeps track of dependencies, which is useful for a large metapackage such as ubuntu-desktop.

---

### Post by Malfet on 2008-06-27
> **Rocket2DMn said:**
> Also, try using aptitude since this keeps track of dependencies, which is useful for a large metapackage such as ubuntu-desktop.

I used aptitude as well - same result :(
Very strange!

---

### Post by Rocket2DMn on 2008-06-27
Can you post your sources.list file for us?
```
cat /etc/apt/sources.list
``` to output it to terminal.  May be easier to ssh the file over to whatever machine you are using right now, unless you are in a terminal based web client.

---

