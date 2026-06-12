---
title: "Upgrading GNOME without installing a newer distribution"
date: 2008-05-11
forum: Desktop Environments
---

### Post by masonchumpia on 2008-05-11
I'm a recent Windows convert running the Ubuntu 7.10 distribution. I would like to upgrade to GNOME 2.22 without having to install the entire 8.04 distribution. Installation of the 8.04 has proved quite problematic in itself while 7.10 installs flawlessly on my machine. I am aware of GARNOME and JHBuild. However, I don't think I yet have the expertise necessary to use these utilities. Could someone explain the basic steps one must go through in order to build and/or install a newer version of GNOME?

---

### Post by #Reistlehr- on 2008-05-12
You can add the 8.04 repositories to your sources.list (/etc/apt/sources.list) and run sudo apt-get update. then install the new version of gnome. then revert sources.list back to the older version for the  7.10 repos. You can even install from source if you wish.

---

### Post by RAOF on 2008-05-12
> **#Reistlehr- said:**
> You can add the 8.04 repositories to your sources.list (/etc/apt/sources.list) and run sudo apt-get update. then install the new version of gnome. then revert sources.list back to the older version for the  7.10 repos. You can even install from source if you wish.

That's a very bad idea; doing this will result in a the equivalent of a broken Hardy upgrade.  A better (but still not particularly good) idea would be to add the Hardy deb-src lines to sources.list and build the various gnome packages against Gutsy.

It's probably going to be easier to troubleshoot why the upgrade manager doesn't cleanly upgrade your system to 8.04 than to build GNOME 2.22 from source.

---

### Post by masonchumpia on 2008-05-12
> **RAOF said:**
> A better (but still not particularly good) idea would be to add the Hardy deb-src lines to sources.list and build the various gnome packages against Gutsy.

What precisely do you mean by this?

---

### Post by HunterThomson on 2008-05-12
how would I go about installing the new gnome form source or .deb package ... just like any other program??? the web site tells me to look to my distro for the other required packages...

---

### Post by RAOF on 2008-05-12
> **masonchumpia said:**
> What precisely do you mean by this?

You'd add a line like 'deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main' to your sources.list (to get the Hardy source packages), and then you would, one by one, run 'sudo apt-get build-dep $GNOME_PACKAGE ; apt-get -b source $GNOME_PACKAGE' for each gnome package (and there are *many*), which would get the build dependencies (if they can be satisfied; some of them won't be most likely) then build the Hardy source package against the Gutsy development chain.  That will give you a bunch of packages that you can install on your Gutsy system.

This sort of process can work reasonably well for one-off packages that you want, but it's not really practical for the whole GNOME stack.  Working out why the upgrade to Hardy doesn't work, and fixing it, will most likely take less time and give you a bunch of extra cool stuff, too.

---

