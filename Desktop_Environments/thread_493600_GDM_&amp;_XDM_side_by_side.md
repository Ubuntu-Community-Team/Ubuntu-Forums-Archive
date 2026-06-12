---
title: "GDM &amp; XDM side by side?"
date: 2007-07-05
forum: Desktop Environments
---

### Post by x1a4 on 2007-07-05
Hi,

Is it possible, and if so how, to run GDM and XDM simultaneously?  I'm running several X servers and would like XDM to be the display manager on one of them.  

Thank you.

---

### Post by dreadlord_chris on 2007-07-06
Start a new session and from the login screen choose XDM

---

### Post by x1a4 on 2007-07-06
> **dreadlord_chris said:**
> Start a new session and from the login screen choose XDM

The login screen is the display manager.  Currently I'm running 3 GDMs (Gnome Display Managers).  I want to replace one of them with the X Display Manager (XDM).  So, when I press Ctr+Alt+F4 (vc0) I'll see GDM, Ctrl+Alt+F5 (vc1) another GDM, and on Ctrl+Alt+F6(vc2) I want XDM.

---

### Post by x1a4 on 2007-07-22
Anyone?  How do I run GDM and XDM side by side?

---

### Post by dreadlord_chris on 2007-07-23
> **x1a4 said:**
> Anyone?  How do I run GDM and XDM side by side?

> 
Multiple display managers can run simultaneously if they are configured to manage different servers; to achieve this, configure the display managers accordingly, edit each of their init scripts in /etc/init.d, and disable the check for a default display manager.


well... it's a start...

---

