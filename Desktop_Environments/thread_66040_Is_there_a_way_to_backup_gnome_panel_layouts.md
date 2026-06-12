---
title: "Is there a way to backup gnome panel layouts?"
date: 2005-09-15
forum: Desktop Environments
---

### Post by idn on 2005-09-15
I had to reinstall ubuntu recently, and I lost my custom panel layouts. I was wondering is there a xml or config file for each panel that I can backup and restore if I have to reinstall in teh future?

---

### Post by 23meg on 2007-03-16
[http://wiki.ubuntu.com/PanelSwitcher](http://wiki.ubuntu.com/PanelSwitcher)

---

### Post by mptpro on 2008-01-18
I was looking for the same thing.

Anyone know how to download panelswitcher?

---

### Post by Shimmy on 2008-01-18
> **mptpro said:**
> I was looking for the same thing.

Anyone know how to download panelswitcher?

You can install it from subversion, but first you need subversion and phyton:
> sudo apt-get install subversion
sudo apt-get install python
And then checkout from subversion:
> svn checkout [http://panelswitcher.googlecode.com/svn/trunk/](http://panelswitcher.googlecode.com/svn/trunk/) panelswitcher-read-only
To run it:
> python panelswitcher-read-only/source/panelswitcher.py

---

