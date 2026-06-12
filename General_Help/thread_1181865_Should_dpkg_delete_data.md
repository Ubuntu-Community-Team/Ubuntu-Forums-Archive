---
title: "Should dpkg delete data?"
date: 2009-06-08
forum: General Help
---

### Post by Flimm on 2009-06-08
When I uninstall a package from Ubuntu using apt-get or aptitude or synaptic, should its user data be deleted as well?
I thought the answer would be "of course not", but apparently users of [Epidermis](http://epidermis.tuxfamily.org) don't agree. According to [this bug report](https://bugs.launchpad.net/epidermis/+bug/373784), Epidermis specific themes (called pigments) are installed into /usr/share/epidermis/pigments. When you uninstall Epidermis, those pigments are not uninstalled, apt-get prints a warning:
```
dpkg - warning: while removing epidermis, directory `/usr/share/epidermis' not empty so not removed.
```

Should apt-get remove user data? Is it possible to make it do so? What exactly is the difference between remove and completely remove in Synaptic?

---

### Post by oldos2er on 2009-06-08
**apt-get remove** uninstalls any program files from /usr, /lib, /etc, and so on, but leaves behind the user's configuration files, which are hidden files in the home directory. Same with Synaptic 'remove.'

 **apt-get purge** will remove all program files and all configuration files too; it's equivalent to Synaptic's 'completely remove.'

---

### Post by sdennie on 2009-06-08
dpkg and apt can only remove things that they are aware of.  If a user has installed extra themes, the only things those tools know about the themes is that they are not part of the original package and so can't be safely removed automatically.

---

### Post by Flimm on 2009-06-08
> **oldos2er said:**
> **apt-get remove** uninstalls any program files from /usr, /lib, /etc, and so on, but leaves behind the user's configuration files, which are hidden files in the home directory. Same with Synaptic 'remove.'

 **apt-get purge** will remove all program files and all configuration files too; it's equivalent to Synaptic's 'completely remove.'Yes, but **apt-get purge** will leave user data (eg: themes) and configuration files found in ~/ , am I correct?

---

