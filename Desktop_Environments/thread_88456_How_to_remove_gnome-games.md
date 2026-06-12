---
title: "How to remove gnome-games?"
date: 2005-11-10
forum: Desktop Environments
---

### Post by washman on 2005-11-10
How to remove /Applications/games ? 

When I used Add Applications, it looked that I have to remove gnome-desktop also, does that matter? Is there another way to remove those games clearly?

THanks in advance.

---

### Post by jeffreyvergara.NET on 2005-11-10
hi, you can use synaptic to remove it. just search for gnome games in Synaptic. ^_^

---

### Post by mostwanted on 2005-11-10
[QUOTE=washman]How to remove /Applications/games ? 

When I used Add Applications, it looked that I have to remove gnome-desktop also, does that matter? Is there another way to remove those games clearly?

THanks in advance.[/QUOTE]

That doesn't matter.

---

### Post by washman on 2005-11-10
[QUOTE=jeffreyvergara.NET]hi, you can use synaptic to remove it. just search for gnome games in Synaptic. ^_^[/QUOTE]

Hi, that's what i said, i have to remove gnome-desktop with it........

---

### Post by washman on 2005-11-10
[QUOTE=mostwanted]That doesn't matter.[/QUOTE]

Thanks, then can you tell me what's the function of gnome-desktop? Is any other program using it?

---

### Post by Pablo_Escobar on 2005-11-10
There are some meta-packages like ubuntu-desktop, which don't do anything themselves, they just are to watch all components of f.e. ubuntu, gnome are in place. I removed the ubuntu desktop package and my Ubuntu works great :D

---

### Post by Miguel on 2005-11-10
Practical info:

You can safely remove it. However, if you want to update to Ubuntu 6.04 using apt-get (instead of a clean reinstall), if might be useful to reinstall it (it will ask for gnome-games, though). 

Theoretical info:

gnome-desktop is a dummy package. What does it mean? It means that it is a basically empty package... with dependencies. These dependencies are provided because, in the case of an upgrade, some new packages or versions could be useful (if they were needed, apt should take care of this). If you update the dummy package and it lists a new package as needed, synaptic will update.

Example (I have written a mess of a theory):

Dummy imaginary package **ubuntu-burner**. Let's imagine this package will install the desired cd burning program by the ubuntu team. So we have **ubuntu-burner v.5.10**, and it lists gnomebaker as a dependency.

Let's suppose now that in ubuntu 6.04 the dev's decide that graveman is a better tool for their needs (and their users'). So **ubuntu-burner v.6.04** will list graveman as a dependency. Perfect. When you upgrade to ubuntu 6.04, you will also update ubuntu-burner from 5.10 to 6.04, and it will install (or update) graveman for you. Of course, you can ignore this package (because it is not essential) and continue using gnomebaker.

Now, you can remove gnome-baker without removing **ubuntu-burner** (if no more packages depend on gnome-baker, that is).

Some dummy packages:
ubuntu-base (you should not ignore this unless you know what you are doing)
ubuntu-artwork
ubuntu-desktop
freeciv (at least in debian)

---

### Post by washman on 2005-11-10
[QUOTE=Miguel]Practical info:

You can safely remove it. However, if you want to update to Ubuntu 6.04 using apt-get (instead of a clean reinstall), if might be useful to reinstall it (it will ask for gnome-games, though). 

Theoretical info:

gnome-desktop is a dummy package. What does it mean? It means that it is a basically empty package... with dependencies. These dependencies are provided because, in the case of an upgrade, some new packages or versions could be useful (if they were needed, apt should take care of this). If you update the dummy package and it lists a new package as needed, synaptic will update.

Example (I have written a mess of a theory):

Dummy imaginary package **ubuntu-burner**. Let's imagine this package will install the desired cd burning program by the ubuntu team. So we have **ubuntu-burner v.5.10**, and it lists gnomebaker as a dependency.

Let's suppose now that in ubuntu 6.04 the dev's decide that graveman is a better tool for their needs (and their users'). So **ubuntu-burner v.6.04** will list graveman as a dependency. Perfect. When you upgrade to ubuntu 6.04, you will also update ubuntu-burner from 5.10 to 6.04, and it will install (or update) graveman for you. Of course, you can ignore this package (because it is not essential) and continue using gnomebaker.

Now, you can remove gnome-baker without removing **ubuntu-burner** (if no more packages depend on gnome-baker, that is).

Some dummy packages:
ubuntu-base (you should not ignore this unless you know what you are doing)
ubuntu-artwork
ubuntu-desktop
freeciv (at least in debian)[/QUOTE]


understood.

That means no matter which default installed program i want to remove, i have to remove ubuntu-desktop with it, and it will not introduce any problem before I upgrade ubuntu to the next version, correct??:KS

---

### Post by Pablo_Escobar on 2005-11-10
Bingo !! :)

---

