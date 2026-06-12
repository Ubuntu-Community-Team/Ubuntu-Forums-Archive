---
title: "rc.local vs bashrc on X/Ubuntu"
date: 2011-10-22
forum: Desktop Environments
---

### Post by erasmus777 on 2011-10-22
I'm new to Xubuntu.  It's a different experience than Ubuntu and so far I'm really enjoying it.

I have an academic question: on Ubuntu, my .bashrc script was executed at first login.  However, on Xubuntu it's not executed until I open the terminal for the first time. IIUC, I should add startup scripts to rc.local.  What is the difference between the two scripts and why do the flavors execute them differently?

Thanks in advance.

---

### Post by gsmanners on 2011-10-22
The rc.local pertains to runlevels and .bashrc is just for when you want a shell. Those are two totally different events. Sounds to me like your install of Ubuntu was running a bash script in its startup (I have no idea why).

---

