---
title: "backup, which files? + some general q's"
date: 2005-12-25
forum: General Help
---

### Post by tsr on 2005-12-25
Ok, so at last I've come around to ditch Windows and start using Ubuntu.

Before I feel comfy with this I need some help/pointers.

1. Which files do I _need_ to backup to be able to restore the system (on the same computer) at it's current state? I've come up with the following list, what's missing?
- my home dir
- some kind of list of wich packages are installed
- configuration files (X, apache, php, ?)
- ??

2. Is it possible to change the interface in the general file-selector-window so that I can write the exact file-path/name in some kind of field without clicking around the whole dir-structure?

3. Are there any options to just see the installed applications in the "add application"-app or do I have to mess with synaptics?

That's it for now, I'll be back :D

---

### Post by kabus on 2005-12-25
[QUOTE=tsr]

1. Which files do I _need_ to backup to be able to restore the system (on the same computer) at it's current state? 
[/QUOTE]

All the configuration files are located either in /etc or your home directory, I think.

> 
2. Is it possible to change the interface in the general file-selector-window so that I can write the exact file-path/name in some kind of field without clicking around the whole dir-structure?


Just press Control-L.

---

### Post by aysiu on 2005-12-25
[QUOTE=tsr]
1. Which files do I _need_ to backup to be able to restore the system (on the same computer) at it's current state? I've come up with the following list, what's missing?
- my home dir
- some kind of list of wich packages are installed
- configuration files (X, apache, php, ?)
- ??[/QUOTE] Its entirely current state? You should probably use something like PartImage (Google it and look in Synaptic) to back up an image of your entire partition's data. Then you can use PartImage to restore it later, too.

---

