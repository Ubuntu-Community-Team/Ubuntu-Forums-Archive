---
title: "Nautilus: Default arrange items manually?"
date: 2011-09-30
forum: Desktop Environments
---

### Post by BadgerKid on 2011-09-30
I'm using lucid, but I think my question applies more generally.

I would like to set the default (icon) view or layout of files to be "arrange manually." Nautilus allows you to set this preference on a per-folder basis, but there is no global option through the preferences menu (Edit -> Preferences -> Default View -> Arrange Items). There does not seem to be a way to apply this setting recursively to subfolders either.

Ideas I looked into: 

1. find where nautilus stores the folder setting information
2. find or perhaps write a nautilus script or shell script
3. look at gconftool for a variable to set
4. web search for 1-3 or keywords involving nautilus, layout, recursive, manual,...

I found where one could set the folder backgrounds recursively but did not find something similar for icon arrangement.

Any thoughts toward a possible solution?

---

### Post by Frogs Hair on 2011-09-30
Nautilus Elementary has some options that the default Nautilus does not and may be worth checking out . The PPA works with some earlier releases .[http://www.linuxnov.com/install-nautilus-elementary-in-ubuntu-11-04-natty-narwhal-ppa/](http://www.linuxnov.com/install-nautilus-elementary-in-ubuntu-11-04-natty-narwhal-ppa/)

---

### Post by alfplayer on 2011-09-30
GConf key **default_use_manual_layout** (it's listed on [http://people.gnome.org/~bmsmith/gconf-docs/C/nautilus.html]("http://people.gnome.org/~bmsmith/gconf-docs/C/nautilus.html")) seems to do it. I haven't checked.

Per-folder settings appear to be stored as GVFS metadata, with attribute **nautilus-icon-view-auto-layout** set to false. Maybe you can set it for all folders you choose from a script using command **gvfs-set-attributes**.

---

