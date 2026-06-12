---
title: "Prevent kernel upgrade using apt-get dist-upgrade"
date: 2006-06-16
forum: Desktop Environments
---

### Post by axely on 2006-06-16
Hi,

Does anyone know how to prevent a kernel upgrade when doing a dist-upgrade or just an upgrade.  What do you put inside of your apt.conf to do so?  The latest kerenl update (25), just made it to where I don't have sound working anymore, however I can still boot into the old kernel (23) and I have sound.  So I was wondering, is there a way to prevent something like the kernel from being upgraded?  This would be especially useful on my LTSP servers.  Thanks!

Axely

---

### Post by jonrkc on 2006-06-16
I, too, would very much like to be able to upgrade without touching the kernel.  I always assumed it wasn't possible, but wondered why.  Now I wonder if I missed something somewhere.

---

### Post by Ramses de Norre on 2006-06-16
I know you can lock versions in synaptic, you probably can do it in a conf file somewhere too but I've never locked something before so I haven't searched for it yet.

I found this for synaptic: > # Open Synaptic (System - Administration - Synaptic Package Manager)
# Scroll down to (or search for) the entry for "package_name"
# Click once on the entry to highlight it, and select the menu option Package - Lock version

---

### Post by jonrkc on 2006-06-16
Thanks, Ramses, I'll try that for the kernel.  (And hope I remember what I did, next time I *do* want to upgrade it.)

---

### Post by axely on 2006-06-16
What about using the apt.conf or the command line?

---

### Post by axely on 2006-06-16
Just wanted to say thanks!  I will try that as well.

---

