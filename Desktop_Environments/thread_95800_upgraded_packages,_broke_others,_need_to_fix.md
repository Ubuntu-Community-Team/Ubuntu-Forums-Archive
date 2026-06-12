---
title: "upgraded packages, broke others, need to fix"
date: 2005-11-27
forum: Desktop Environments
---

### Post by timczer on 2005-11-27
In a misguided effort to install mondorescue (used their repositroy version because the debian version server was down) I ended up upgrading a couple of packages.  Specifically libstdc++6 and gcc-4.0 -base to the newer versions of 4.02.  Now other packages that depended on the older 4.01 are coming back as broken. (cpp-4.0, g++-4.0, gcc-4.0, gij-4.0, libgcj6, libstdc++6-4.0-dev).  If I try to force a downgrade of the two upgraded packages to the old versions, it requires removing a ton of other packages.  

Is there anyway to downgrade these packages without removing all the other ones first, or would it be better to upgrade the broken packages to the same 4.02 level?  Will this end up breaking the long list of packages that seem to depend on these other six packages or will they still work with the new installed packages?

---

### Post by Xian on 2005-11-27
I would first try using aptitude to downgrade those packages.
The format is below:

$ sudo aptitude install <pkgname>=<version>

---

### Post by timczer on 2005-11-27
Unfortunately I do not currently have aptitude installed.  If I try to install it through apt-get or through synaptic, I get the same list of programs to be removed.

---

### Post by timczer on 2005-11-27
Never mind.  I tried the same idea through apt-get and it worked.  I did sudo apt-get -f install libstdc++6=4.0.1-4ubunutu9 gcc-4.0-base=4ubuntu9 and it downgraded those packages and synaptic no longer shows any broken packages.  Thanks for the help.

---

