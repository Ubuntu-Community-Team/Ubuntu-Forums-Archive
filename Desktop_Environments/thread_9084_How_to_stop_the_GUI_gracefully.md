---
title: "How to stop the GUI gracefully?"
date: 2004-12-23
forum: Desktop Environments
---

### Post by Rottweiler on 2004-12-23
What is the preferred way to stop the GUI (Gnome, et al) gracefully?
  
  All the runlevels appear to start gdm (why?). Or is there a runlevel that is multiuser without X and Gnome?
  
  Is it as simple as '/etc/init.d/gdm stop'?
  
  Thanks.

---

### Post by varunus on 2004-12-24
Just log out and do what you said (/etc/init.d/gdm stop).  This should bring you to a console.  Another way to do this is to execute "sudo init 1".  This will take you to single user mode.

---

