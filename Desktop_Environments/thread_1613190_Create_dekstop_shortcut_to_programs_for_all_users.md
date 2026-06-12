---
title: "Create dekstop shortcut to programs for all users"
date: 2010-11-04
forum: Desktop Environments
---

### Post by chrisdee on 2010-11-04
Hello.

Does someone know how to create desktop shortcuts to programs (e.g to rdesktop) to all users on Ubuntu 10.04 ?

Where (in which file) do I put the shortcut so it will appare (clickable) on the dekstop for all users logging into the machine ?

Thanks

---

### Post by chrisdee on 2010-11-15
Nevermind, I found a solution. 

I created a launcher on the desktop. I copied this launcher from /home/myUser/Desktop/ to /etc/skel/.

Now anybody new logging into the system gets the shortcut from /etc/skel/.



If anybody wants to copy the desktop preferences so that all new users gets the same settings, they also have to copy the /home/myUser/.gconf folder to /etc/skel/ aswell.

---

