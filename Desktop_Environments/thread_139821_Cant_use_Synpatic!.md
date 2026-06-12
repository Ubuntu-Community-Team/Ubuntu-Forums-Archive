---
title: "Cant use Synpatic!"
date: 2006-03-04
forum: Desktop Environments
---

### Post by KevNice on 2006-03-04
OK, I tried to get into the Package Manager, typed in my pass, and I got this message:

"Failed to run /usr/sbin/synaptic as user root:
Unable to copy the user's Xauthorization file".

Does this have something to do with me changing the permissions in the /tmp folder using "sudo chmod 1777" when Ubuntu wouldnt start up? This is the first time I've tried to run Synpatic since getting back into the desktop, never had this problem before..

---

### Post by weijie90 on 2006-03-04
why not chmod /tmp to its original permissions?

btw, why couldn't ubuntu start up?

---

### Post by Xian on 2006-03-04
Try renaming the /home/<username>/.Xauthority file.
Then logout/login. It should create a new file and fix the issue.

---

### Post by KevNice on 2006-03-07
I don't know /tmp folder's original permissions, but..

I had to do sudo chmod 1777 /tmp for another issue, and it seems to have cleared up the synaptic error as well.. hmm... mysterious..

---

