---
title: "I can't install Flash player!!!"
date: 2009-05-03
forum: General Help
---

### Post by jasmrael on 2009-05-03
I'm new in this so please help. I've tried to install Flash Player but appears: Error: Dependency is not satisfiable: libpango.0-0
What can I do?
thnx

---

### Post by CatKiller on 2009-05-03
You could install libpango.

How are you trying to install Flash? By far the easiest way to install it is to install the *flashplugin-installer* package (from the multiverse repository) if you're on 9.04, or *flashplugin-nonfree* for earlier versions. This will sort out any dependencies automatically.

System -> Administration -> Software Sources to enable the multiverse repository.

System -> Administration -> Synaptic Package Manager to install the packages you need.

---

