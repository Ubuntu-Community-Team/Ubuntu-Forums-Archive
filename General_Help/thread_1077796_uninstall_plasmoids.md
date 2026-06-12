---
title: "uninstall plasmoids?"
date: 2009-02-22
forum: General Help
---

### Post by aginsa on 2009-02-22
hi. i'm following [these instrucions]("http://www.kubuntu.org/news/kde-4.2") to upgrade to kde4.2, and it says to uninstall any plasmoid because they are not compatible with the new kde4.2. so how do i remove plasmoids? i don't think uninstalling the kdeplasma-addons from the package manager is a good idea because i will and with a blank desktop. any other way how to delete just the widgets?
thanks

---

### Post by knattlhuber on 2009-02-22
See here:
[http://ubuntuforums.org/showthread.php?t=878457]("http://ubuntuforums.org/showthread.php?t=878457")

---

### Post by snova on 2009-02-22
> **aginsa said:**
> hi. i'm following [these instrucions]("http://www.kubuntu.org/news/kde-4.2") to upgrade to kde4.2, and it says to uninstall any plasmoid because they are not compatible with the new kde4.2. so how do i remove plasmoids? i don't think uninstalling the kdeplasma-addons from the package manager is a good idea because i will and with a blank desktop. any other way how to delete just the widgets?
thanks

Anything installed through the package manager will be upgraded transparently, they are no concern. I believe it only applies to Plasmoids you install yourself, from source.

As long as you haven't installed anything from external sources, there is nothing you need to do.

---

### Post by abn91c on 2009-02-22
I didnt have to uninstall the plasmoids to upgrade to 4.2, all I did was close all of the ones I had running(clock, weather, desktop forlder)then upgraded, Dell GX240

---

### Post by aginsa on 2009-02-23
i don't have any other plasmoid just those which were installed by default, so i'm going to upgrade now and see what i come through, Thanks

---

### Post by masterkoppa on 2009-03-11
I know this is an old post, but just for future reference to uninstall a plasmoid all you need to do is open a terminal and type
```
plamapkg -r <plasmoid-name>
```

If the plasmoid has a space in his name usually a "-" between the words will do.

---

### Post by sophie27 on 2009-04-30
I guess you missed an "s"

plasmapkg -r <plasmoid-name>

---

