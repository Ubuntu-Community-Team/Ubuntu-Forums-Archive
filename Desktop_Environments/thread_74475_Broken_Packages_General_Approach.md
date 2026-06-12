---
title: "Broken Packages: General Approach?"
date: 2005-10-11
forum: Desktop Environments
---

### Post by N6546R on 2005-10-11
I have a few broken packages on my system (was Hoary, now Breezy) such as yakuake and wlassistant. When I install or upgrade packages, synaptic/adept insist on removing the broken packages first. What I do now is just allow the package manager to remove them, then I reinstall them with dpkg. In each case there are unmet and apparently unresolvable package dependencies, but the applications themselves work just fine.

Is there a simpler way to handle these oddballs? Maybe repackage them?

Perry

---

### Post by mlomker on 2005-10-11
> Is there a simpler way to handle these oddballs? Maybe repackage them?


There's always the option of compiling them from source.  Once compiled you can create your own .deb package using **checkinstall** or dh_make if you wish.  I often just install the package without creating a .deb.  If dpkg doesn't know about the program then it won't bother you about it.

---

### Post by N6546R on 2005-10-12
[QUOTE=mlomker]There's always the option of compiling them from source.  Once compiled you can create your own .deb package using **checkinstall** or dh_make if you wish.  I often just install the package without creating a .deb.  If dpkg doesn't know about the program then it won't bother you about it.[/QUOTE]

checkinstall works great, thanks for the tip. 

Perry

---

