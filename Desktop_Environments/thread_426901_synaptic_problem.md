---
title: "synaptic problem"
date: 2007-04-28
forum: Desktop Environments
---

### Post by bearcat on 2007-04-28
Having a problem with Synaptic packages. 

The package vmware-kernel-modules-2.6.17-11 has gotten flagged for removal, but when I try to apply changes I get the following error message:

> E: vmware-player-kernel-modules-2.6.17-11: subprocess post-removal script returned error exit status 139

The problem is that I'm trying to install another package, and this error message shuts down the process before the new package installs. And the vmware package won't let me unflag it or reinstall it, either, meaning that I'm effectively frozen out of being able to install or remove *anything* else with Synaptic.

Anybody know how I can fix this?

And yes, I've already tried "apt-get install -f".

---

### Post by StarsAndBars14 on 2007-04-28
I remember seeing that when my files were flagged as "immutable" and Synaptic tried to remove them.

See if a "chattr -i <new/package/directory/here>" does the trick.

---

### Post by bearcat on 2007-05-05
I actually ended up rebooting into an older kernel and deleting the file from there. Everything cleared up after that.

---

