---
title: "Install Gnome, Uninstall KDE (Kubuntu &gt; Ubuntu)"
date: 2008-08-29
forum: Desktop Environments
---

### Post by blairbeckwith on 2008-08-29
Hey guys,

My father installed Kubuntu by accident on my computer, when I wanted Ubuntu.  Are there terminal commands I can use to remove KDE and affiliated programs, and install Gnome?

Basically, I want to move from Kubuntu to a vanilla Ubuntu install, without reinstalling Ubuntu.

Thanks in advance!

EDIT: I figured out how to install Gnome (sudo apt-get install ubuntu-desktop), but am still trying to figure out how to remove KDE and all affiliated programs.

---

### Post by kellemes on 2008-08-29
```
sudo apt-get remove kubuntu-desktop
sudo apt-get install ubuntu-desktop
```
Should do it.

---

### Post by Seisen on 2008-08-29
I think this is what you are looking for 

[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

---

### Post by blairbeckwith on 2008-08-29
> **Seisen said:**
> I think this is what you are looking for 

[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

PERFECT! Thanks! I found similar instructions for older versions, but this was just it! Thanks!

---

