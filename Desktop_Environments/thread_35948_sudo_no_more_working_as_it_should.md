---
title: "sudo no more working as it should"
date: 2005-05-21
forum: Desktop Environments
---

### Post by blakken on 2005-05-21
I recently noticed that action sudo followed by a command (for instance sudo synaptic) doesn't ask me no more password !
I did some sudo -k then restarted the previous command but no more password asking?
Here is my /etc/sudoers file:
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

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) NOPASSWD:ALL


Please help ,my sytem is totally unsecured!  ](*,)

---

### Post by bored2k on 2005-05-21
```
export EDITOR=gedit && sudo visudo
```
```
# sudoers file.
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults    !lecture,tty_tickets

# User privilege specification
root    ALL=(ALL) ALL

# Added by Ubuntu installer
yourusername    ALL=(ALL) ALL

```

---

