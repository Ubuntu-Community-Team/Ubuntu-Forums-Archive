---
title: "[SOLVED] KDE 4.1.2 installation?"
date: 2008-10-12
forum: Desktop Environments
---

### Post by armageddon08 on 2008-10-12
When I install KDE 4.1.2 using the command ```
sudo aptitude install kubuntu-kde4-desktop
``` many the extra apps that get installed with it.
How do I install KDE without them?

---

### Post by sokopok on 2008-10-12
You could instead install kdebase-runtime, this will install a minimal set of kde support apps/libs. Then add other things you like/need.
Alternatively just install the specific kde application you want, the package manager will install dependecies for you.

---

### Post by armageddon08 on 2008-10-12
> **sokopok said:**
> You could instead install kdebase-runtime, this will install a minimal set of kde support apps/libs. Then add other things you like/need.
Alternatively just install the specific kde application you want, the package manager will install dependecies for you.
Most of the GNOME applications work fine on KDE4. So it does not make sense to have two sets of applications for the same task. I would like to have the KDE4 DE and not the entire application set.

---

### Post by benerivo on 2008-10-12
> **armageddon08 said:**
> When I install KDE 4.1.2 using the command ```
sudo aptitude install kubuntu-kde4-desktop
``` many the extra apps that get installed with it.
How do I install KDE without them?

To just get the minimal kde4 desktop try```
sudo apt-get install kdebase-kde4
```

---

### Post by armageddon08 on 2008-10-13
> **benerivo said:**
> To just get the minimal kde4 desktop try```
sudo apt-get install kdebase-kde4
```

It didn't work. Whenever I try to login to my KDE4 desktop it gives some error and says something like could not find/start startkde , falling back to default and then it starts GNOME.

---

### Post by armageddon08 on 2008-10-13
Isn't there any way I can install minimal KDE4?

---

### Post by benerivo on 2008-10-13
kdebase-kde4 must be missing something. Have a look through synaptic and see what other minimal packages are there. The right one might now be called something like  kde4-core. I'm sure there will be a minimal package that will do the job, however kdebase-kde4 is probably only one package away from making it start. Maybe kde4-workspace, or something like that.

---

### Post by armageddon08 on 2008-10-13
> **benerivo said:**
> kdebase-kde4 must be missing something. Have a look through synaptic and see what other minimal packages are there. The right one might now be called something like  kde4-core. I'm sure there will be a minimal package that will do the job, however kdebase-kde4 is probably only one package away from making it start. Maybe kde4-workspace, or something like that.
Okay....I'm now installing kde4-core and i'm feeling it's gonna go right this time!:)

EDIT: Hey it worked....thanks! I'll now install a minimal set of kde4 alternatives to applications which I use most.

---

