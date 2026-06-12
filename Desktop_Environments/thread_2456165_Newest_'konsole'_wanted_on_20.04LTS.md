---
title: "Newest 'konsole' wanted on 20.04LTS"
date: 2021-01-05
forum: Desktop Environments
---

### Post by l1knox on 2021-01-05
'konsole', the KDE termnial application, has been given "focus follows mouse" support in its newest version (Dec 2020 I believe).  "focus follows mouse" is within the application, not as a window manager feature.

I very much want this feature.

Is there any way to get that new version of 'konsole' on 20.04 LTS ?

---

### Post by CatKiller on 2021-01-06
Really what you want is KDE Neon.

The Ubuntu policies, which allow for the flavours to update the packages in the repositories as needed for bugfixes and security updates, don't allow for the packages to be updated for new features except in very limited circumstances - the SRU process. That means that Kubuntu, the same as the other flavours, stays on a fixed version of the desktop environment for the lifetime of the release.

KDE Neon (which is maintained by the KDE devs) uses the same Ubuntu base as Kubuntu does, but they use their own repository for the KDE parts instead of using the Ubuntu ones. That gives them the flexibility to upgrade those packages whenever they want, and for whatever reason they want.

---

### Post by l1knox on 2021-01-07
I don't use KDE as my desktop environment, just konsole (and the packages it requires).  I wish there was some way to magic that feature across (I don't need the cosmetic features, it's the functional "focus follows mouse" bit I want).

I hoped (fingers crossed) a KDE Ubuntu user had ported that konsole back from 'neon' some how.

---

### Post by CatKiller on 2021-01-07
KDE, more than most desktop environments, benefits from everything working together; all the applications at a particular point in time will be using the same version of the KDE frameworks. You could certainly try getting a deb or compiling the new version of konsole, but you'll likely have a lot of dependencies to manage as well. 

If you're not using KDE there's fewer things to break by adding the KDE Neon repository, which will have the newer konsole and the newer KDE frameworks. The KDE devs don't say that doing that *won't* work, but they advise against it. People that have tried adding that to Kubuntu have reported having to fiddle some version conflicts, but you wouldn't have those packages to conflict in the first place. Or at least, not as many. 

If you do try it, back up anything important first, just in case. 

As an alternative, you could try applying the patch that gives that feature from the version of konsole that has it to the version of konsole that you're using and compile it for yourself. The same again, though, that how easy that is depends on which other things in other packages might be needed for that feature to work.

---

### Post by ActionParsnip on 2021-01-08
Plenty of PPAs if you want the newer desktop environment. The newer Konsole will have a tonne of deps for the KDE version it is in so you'll be pretty much upgrading your entire DE rather than just Konsole. The tow are pretty intertwined

---

