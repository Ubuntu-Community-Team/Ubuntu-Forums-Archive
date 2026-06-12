---
title: "HELP! Update Manager won't update."
date: 2010-07-27
forum: Desktop Environments
---

### Post by Mugsy323 on 2010-07-27
I'm running 32bit Ubuntu 10.04. When I boot, Update Manger says it has 16 packages waiting to be installed, but when I try to install them, I get the following message:
[INDENT]"trying to recover from package failure"[/INDENT]
...followed by an error message that the packages "could not be installed".

The first thing I tried was to just update each package individually, which made no difference.

Next, I tried wiping out the packages (sudo rm -vf /var/lib/apt/lists/*) and letting UM download them again. Same thing.

I tried installing the packages using "sudo apt-get update", but got the same error as before.

Suspecting possible trouble with the file system, I forced a disk check using "sudo touch /forcefsck" and rebooting, which found nothing wrong.

I'm out of ideas. Anyone?

---

### Post by randywilharm on 2010-07-27
I would look for broken packages in Synaptic and fix them from there.

No code-- do everything from Synaptic GUI.

---

