---
title: "Change to root user via VNC?"
date: 2009-01-05
forum: Desktop Environments
---

### Post by davoutuk on 2009-01-05
I have a ubuntu desktop installation on an old PC. I've set this up so that the desktop auto logs in as user 'linux'. 

There is no screen or keyboard attached. I use VNC from another Windows desktop to access the linux machine.

Even though I haver the 'linux' user set up as an administrator it seems that for some operations I need to be signed in as the 'root' user. 

Via VNC how can I change the user from 'linux' to 'root'?  

I've tried using the 'switch user' option from the GUI panel that offers log out/restart/shot down options, but once I select this my VNC screen goes blank. 

Alternatively how can I configure VNC so that it accesses the linux machine via the root user?

P.S. I'm a linux newbiee so please provide 'idiot level' steps to any answers.

---

### Post by jken146 on 2009-01-05
You don't need to log in as root.  Anything that root can do can be done by the first user you created (and his own password) using sudo.

Examples:
In a terminal: ```
sudo apt-get install abiword
``` installs Abiword.
```
sudo -i
``` gives you a 'root' prompt.
```
gksu gedit /etc/fstab
``` lets you edit the file /etc/fstab in the text editor gedit.

---

