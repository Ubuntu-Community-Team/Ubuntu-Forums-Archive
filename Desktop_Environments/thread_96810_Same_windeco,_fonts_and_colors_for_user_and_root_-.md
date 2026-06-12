---
title: "Same windeco, fonts and colors for user and root - how?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by z-vet on 2005-11-29
Hi all.
Programs that i run as root have a different colors, fonts and windeco. GTK apps are affected too and i don't like it at all. How can i make all my desktop - for user and for root - to have a same look?

---

### Post by ace2005 on 2005-11-29
Running "sudo firestarter" makes firestarter look like all the other apps instead of what root apps look like

Or you could just login as root and change it to look like you're account but i have not tried this

---

### Post by Ptero-4 on 2005-11-29
for having the same look and feel in gtk apps go to kcontrol and in Look & feel>gtk select the options that say "use current kstyle/windeco" or something for that style (Can't recall right now, havent install KDE/Mac on my OS X box yet, I was waiting for KDE 3.5 to come out). and for using the same kstyle on the root user (root uses your current windeco, is the kstyle what changes) open the run box from the kmenu and type "kdesu kcontrol", put your password when it asks and kcontrol will open as root (notice the different kstyle, that's the sign that it's running as root), set your preferred kstyle and set the two settings above in Look & feel>gtk as well, close kcontrol. That's it both root and your user account have the same kstyle and both root and your user account force gtk apps to use your kstyle as gtk theme.

---

### Post by z-vet on 2005-11-29
Thanks!

---

