---
title: "Preventing evolution services from starting?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by naked on 2006-01-15
I don't use evolution, so how can I keep 'it' from starting?  Things like evolution-data-server etc... are taking up my memory!

Thanks.

L

---

### Post by RAOF on 2006-01-15
All sorts of things, like various gnome-panel bits, rely on evolution-data-server.  It started out as just for evolution, but it's become a more general-purpose repository.

---

### Post by naked on 2006-01-16
Where can I find out what these other 'bits' are at?  All the various evolution things take up 100-150m of my memory, I'd like to have that available.

I just terminate the evolution processes on reboot and haven't noticed any problems or them coming back.

As little bits aside, how do I stop them from starting?

L

---

### Post by RAOF on 2006-01-16
If you don't want to use evolution, you could just uninstall it through synaptic/apt-get.  It will also want to remove the "ubuntu-desktop" package.  Don't worry about that - ubuntu-desktop is an empty package which just depends on all the default programs installed (this is so you can just install ubuntu-desktop and get the basic, default ubuntu system).

Don't remove evolution-data-server.  It will stop your panels from working.

If you ever want to upgrade to the next version of Ubuntu, you should re-install ubuntu-desktop before you do.  That way, all the new programs in the default install will get pulled in.

---

