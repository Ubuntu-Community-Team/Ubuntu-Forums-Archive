---
title: "Error with auto-update"
date: 2009-01-09
forum: General Help
---

### Post by Colin@oxford on 2009-01-09
I ran the auto-updates on my 8.04 (Hardy) this morning and received these errors at the end:

E: linux-ubuntu-modules-2.6.24-23-generic: subprocess post-installation script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-23-rt: subprocess post-installation script returned error exit status 1
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-image-rt: dependency problems - leaving unconfigured
E: linux-rt: dependency problems - leaving unconfigured

is there any way of finding out what caused the error?
What should I do now?

---

### Post by Colin@oxford on 2009-01-09
Oh forget it - I have just seen the full messages in the scrteen behind - out of space!

---

### Post by thedarkwinter on 2009-01-09
Out of space? Hard drive space? You definitely need to clean up then using the usual method of deleting what you don't need.

Also, running ```
apt-get clean
``` will flush the download cache for apt, which may help. (But you will have to re-download these files again.

You can probably just run ```
apt-get update (or dist-upgrade)
``` in the terminal again afterwards to try again. If that doesn't work it will give you a suggestion.

cheers,
michael

---

### Post by Colin@oxford on 2009-01-09
It is the boot partition that is too small.  One too many kernels left in there.  I have now attempted to delete the oldest of them but now Synaptic is stuck thinking that it still needs to be deleted, but when attempting to do so finds that it is not there.

Where is the file that Synaptic keeps telling it what actions are still pending?  It does not forget this mis-information after a restart, so it must be somewhere on disk!

---

### Post by Colin@oxford on 2009-01-09
To answer my own question (again):  I removed some (empty) files from /var/lib/dpkg/info and that appears to have cured the problem

---

