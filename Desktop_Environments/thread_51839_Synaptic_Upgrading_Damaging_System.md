---
title: "Synaptic Upgrading Damaging System"
date: 2005-07-25
forum: Desktop Environments
---

### Post by jpoe on 2005-07-25
Hi all,

This is the second time in two days that installing a recommended upgrade (the box that pops up in the upper right corner by default) has damaged a program on my system.  Yesterday a new version of firefox came out; and after I upgraded it (no go, seg faukt).  Luckily in the repositories there are a few versions of firefox and one of the others worked ...


..Today it told me gDesklets needed upgraded, so I abliged; and now it won't start (or rather, starts then instantly takes 99.9% CPU and does nothing).  

I don't really have any unusual setup, and am only using the normal hoary universe/multiverse/backport/tamir repositories.  I guess my question is anyone else having such problems, and more importantly, is there anyway to uninstall a new version and install the slightly older version you were using previously?

Thanks


I'm using the Hoary repositories because I am actually running a Hoary system on this particular machine.

---

### Post by jasmuz on 2005-07-25
The newest version of FF offered via the Backports had issues, so it was removed, we recommend you downgrade to the normal version.
Regarding th gDesklets, remove the .gdesklets directory in you /home, and restart it.

---

### Post by grim42 on 2005-07-25
Don't know about gdesklets, but the firefox problem is widespread -- do a quick search and you'll see that everyone had that problem.

---

### Post by jpoe on 2005-07-25
Hi,

Thanks for the super fast response; thats why I love this community.  Anyway, your advice worked like a charm.  But, I am still wondering if I need to in the future, is there any simple way to downgrade to the previous version I was using.

In the case of firefox its pretty simple because there are several simulataneous versions available; but for like gDesklets the only one available (via Synaptic) is the newest version.

Thanks again for all your help,

James

---

### Post by grim42 on 2005-07-25
If you have the Ubuntu CD handy you can find the original deb file on there and use dpkg to install it. See *man dpkg* for more information.

---

