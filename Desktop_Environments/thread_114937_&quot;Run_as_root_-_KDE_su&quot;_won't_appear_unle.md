---
title: "&quot;Run as root - KDE su&quot; won't appear unless..."
date: 2006-01-09
forum: Desktop Environments
---

### Post by bagofchickens on 2006-01-09
Hi guys, I've noticed that sometimes when I try to call through the menus Adept, or Synaptic, or any other program normally executed with root privileges, I get nothing at all. The thing is, when I start The GIMP immediately after this happens, the "Run as root - KDE su" dialog suddenly pops up. "sudo adept" and "sudo kcontrol" under the command line, for instance, always do the trick though. Maybe I did something wrong playing around with the system, but is there any way of going around this one? It's very annoying...

Almost freshly installed Kubuntu 5.10.

---

### Post by GoldBuggie on 2006-01-09
I do not know if this is the solution to your problem since I have not seen it before but to get correct usage of kdesu and sudo add your user to **/etc/sudoers** in the followin way
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
** <username>      ALL=(ALL) ALL**

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
** <username>      ALL=(ALL) ALL**
``` 
Maybe this will help your problem

---

### Post by bagofchickens on 2006-01-09
I forgot to mention that after restart everything works fine, and I am really not sure what exactly triggers this behavior. Well, I edited /etc/sudoers, but right now there's no way to tell whether the problem has disappeared or not. I'll wait and see, hope your advice works, thanks.

---

