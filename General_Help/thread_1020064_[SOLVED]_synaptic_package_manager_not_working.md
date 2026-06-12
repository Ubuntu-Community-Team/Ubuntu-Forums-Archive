---
title: "[SOLVED] synaptic package manager not working??"
date: 2008-12-23
forum: General Help
---

### Post by rixtr66 on 2008-12-23
My synaptic stopped working after a bad shut down,in ubuntu studio 8.04
now i cant uninstall or install without a dpkg error,file not found?
is there a way to reinstall synaptic?maybe a way to fix it?
any help would be appreciated!!!
Rick:confused:

---

### Post by Talon2 on 2008-12-23
I'm looking for an answer to a problem that sounds similar to yours.

When I start Synaptic a dialog come up that shows this:

---
E: The package hl5050lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
---

When I click on Close (which is the only option on the dialog) Synaptic dies.  There is no way to run it.

How on earth do you fix something like this?

---

### Post by jerome1232 on 2008-12-23
> **rixtr66 said:**
> My synaptic stopped working after a bad shut down,in ubuntu studio 8.04
now i cant uninstall or install without a dpkg error,file not found?
is there a way to reinstall synaptic?maybe a way to fix it?
any help would be appreciated!!!
Rick:confused:

What is the exact error message your getting?

> **Talon2 said:**
> I'm looking for an answer to a problem that sounds similar to yours.

When I start Synaptic a dialog come up that shows this:

---
E: The package hl5050lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
---

When I click on Close (which is the only option on the dialog) Synaptic dies.  There is no way to run it.

How on earth do you fix something like this?

I would probably try and install that package it says must be reinstalled.

```
sudo apt-get install hl5050lpr
```

---

### Post by rixtr66 on 2008-12-24
the package manager was seriously damaged from the unexpected shut down.
so i reinstalled!kinda drastic but it worked.no problems now.
thanks though!!
Rick

---

### Post by jerome1232 on 2008-12-24
> **rixtr66 said:**
> the package manager was seriously damaged from the unexpected shut down.
so i reinstalled!kinda drastic but it worked.no problems now.
thanks though!!
Rick

Usually when dpkg get's interupted you can do this command to fix it (says something about it in the error message)

```
sudo dpkg --configure -a
```

But hey I've reinstalled just because I randomly wanted to try out a new partitioning scheme lol.

---

