---
title: "Why does the kde package depend on kdegames?"
date: 2005-04-26
forum: Desktop Environments
---

### Post by reuben on 2005-04-26
Using synaptic, I'm unable to remove the kdegames package without removing "kde" itself. Why is it set up that way?

Thanks!

---

### Post by poofyhairguy on 2005-04-27
[QUOTE=reuben]Using synaptic, I'm unable to remove the kdegames package without removing "kde" itself. Why is it set up that way?

Thanks![/QUOTE]


Because "KDE" is a metapackage. That means that its a package taht refer to other packages to makes things easier to install. In teh case of "KDE" it exists so that you can go "sudo apt-get install KDE" and get a working desktop instead of having to install every app seperately. Its no big deal to remove it, KDE won't go away.

Kubuntu-desktop is another metapackage.

---

