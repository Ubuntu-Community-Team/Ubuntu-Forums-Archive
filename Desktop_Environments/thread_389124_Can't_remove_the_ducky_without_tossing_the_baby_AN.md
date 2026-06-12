---
title: "Can't remove the ducky without tossing the baby AND the water"
date: 2007-03-20
forum: Desktop Environments
---

### Post by jbeiter on 2007-03-20
There is one thing about Ubuntu that has been bothering me and perhaps there is an easy way around it that I can't see.

It seems like I keep running into applications that are installed that I can't remove (via synaptic) without also removing major applications they are a part of.

For example, this week's system update patches ktorrent. I have no reason that I can imagine for wanting bit torrent at all, KDE's version or otherwise. When I went to remove it though, synaptic also decided I had to remove kde-desktop as well... which I would like to keep.

Is this a limitation with Ubuntu that you pay to have easier administration or is there a trick around this?

I'm a long term unix/linux user... fairly new to Ubuntu.

---

### Post by ardchoille42 on 2007-03-20
> **jbeiter said:**
> There is one thing about Ubuntu that has been bothering me and perhaps there is an easy way around it that I can't see.

It seems like I keep running into applications that are installed that I can't remove (via synaptic) without also removing major applications they are a part of.

For example, this week's system update patches ktorrent. I have no reason that I can imagine for wanting bit torrent at all, KDE's version or otherwise. When I went to remove it though, synaptic also decided I had to remove kde-desktop as well... which I would like to keep.

Is this a limitation with Ubuntu that you pay to have easier administration or is there a trick around this?

I'm a long term unix/linux user... fairly new to Ubuntu.

There are a number of packages that are metapackages. A metapackage exists solely to pull in other packages and dependencies. For example, if I ran kde and wanted to install gnome, I'd have to install tons of packages and maybe hunt down depencies in order to get a properly working gnome desktop. Or, I could just install ubuntu-desktop (a metapackage) and have the package manager pull in all packages and deps required for a properly working gnome desktop. kbuntu-desktop is also a meta package, it simply pulls in all packages and deps required for a properly working kde desktop. metapackages can be uninstalled safely because uninstalling a meta package does not uninstall all the apps that package pulled in. Some of the meta packages I have uninstalled are ubuntu-desktop, ubuntu-minimal and ubuntu-standard. You can open synaptic and look at the package description to see if a package is a meta package or not.

If you're wanting to uninstall an app, but synaptic is telling you that blah-blah (a metapackage) will also be uninstalled, then that is normal for Ubuntu and you can safely uninstall the app and the metapackage without affecting the rest of the system.

Meta packages can be uninstalled and it will not affect the system. The only thing that will be affected is your ability to upgrade to a newer Ubuntu release, you have to re-install all the meta packages you uninstalled and then upgrade.

---

