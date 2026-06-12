---
title: "Is it really safe to remove package ubuntu-mate-desktop?"
date: 2015-06-25
forum: Desktop Environments
---

### Post by nargaroth_reg on 2015-06-25
When attempting to uninstall some applications that come with ubuntu mate 14.04 and I don't use like brasero and cheese using synaptic it tells me that the package ubuntu-mate-desktop has to be removed as well. I checked the description of that package and it says it is safe to remove it, but I'd like to know if someone else has already tried and everything was still working afterwards.

---

### Post by kerry_s on 2015-06-25
yes, safe to remove. i removed mine not to long ago.

---

### Post by Dennis N on 2015-06-25
Yes, I consider it safe. It removes no software from your computer. I've done it myself with similar packages like xubuntu-desktop and lubuntu-desktop. Look up the term 'metapackage' to get more information - ubuntu-mate-desktop is a metapackage.  

Here is some information from apt-cache:
```
dmn@Sydney:~$ apt-cache show ubuntu-mate-desktop
Package: ubuntu-mate-desktop
Priority: optional
Section: universe/[COLOR="#FF0000"]metapackages[/COLOR]
Description-en: Ubuntu MATE - full desktop
 This package is the Ubuntu MATE desktop environment.
 .
[COLOR="#FF0000"]It is safe to remove this package if some of these packages are not desired.[/COLOR]

```

---

### Post by ajgreeny on 2015-06-25
All of the *.desktop packages are metapackages.  These are not applications themselves; they are simply a list of packages that are dependencies of the .desktop package and must be installed if that .desktop package remains, therefore if you remove one of those dependency packages, the *.desktop package will also be removed.

The one time that it is important is if and when you do an online distro upgrade using the package manager, eg from Trusty to Utopic, but if you don't use that upgrade path, you need not worry.

---

### Post by nargaroth_reg on 2015-06-27
Thanks for the replies.
> **ajgreeny said:**
> The one time that it is important is if and when you do an online distro upgrade using the package manager, eg from Trusty to Utopic, but if you don't use that upgrade path, you need not worry.
Why is it important in that case?

---

### Post by bapoumba on 2015-06-27
Meta-packages are no application packages by themselves. They are here to tie the chosen desktop packages all together via dependencies. That means all desktop application versions within a particular release are the ones decided for that release. On an upgrade, the meta-packages ensure all apps or packages are upgraded to their newer version for that upgraded release.

If you remove the desktop meta-package, version upgrade may or may not work, depending on what you have removed/installed in the meantime. You may end up with conflict libraries versions at best. If I am not desperately trying to reclaim hard drive space, I keep the meta-package _and_ the applications I do not use.

---

