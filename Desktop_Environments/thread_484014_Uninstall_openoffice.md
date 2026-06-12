---
title: "Uninstall openoffice?"
date: 2007-06-25
forum: Desktop Environments
---

### Post by Saubazi on 2007-06-25
I am having a standalone system with edgy on it and I don't need lots of this "standard" stuff on it so I thought of uninstalling bits and pieces of it - I tried to uninstall openoffice and got shivers when it told me that it wants to uninstall ubuntu-desktop?!?! What does this mean - it sounded a bit grave or is ubuntu-desktop just some defination package that sort of simpy contains all subparts? Can I let it install ubuntu-desktop and not notice any difference?

---

### Post by tgoose on 2007-06-25
All ubuntu-desktop does is ensure that you have all the default packages. Since openoffice.org is one of the default packages, removing it means you can't have ubuntu-desktop!

There should be no problem with this - I've taken plenty of standard packages off and have no issues whatsoever.

---

### Post by corney91 on 2007-06-25
'apt-cache show ubuntu-desktop' claims:
> It is also used to help ensure proper upgrades, so it is recommended that
 it not be removed.
But I guess in practice it's not really that important if it can be uninstalled.

---

### Post by MarilenCorciovei on 2007-06-26
You should have no pb doing that. Check this: [http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/replace-openoffice/view]("http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/replace-openoffice/view")

In short you just have to find the openoffice packages and remove them:

for  i in $(dpkg --list | grep ii | grep openoffice | cut -c5-35); do apt-get remove $i; done

---

