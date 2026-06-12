---
title: "Can't 'unlock' PolicyKit or Users &amp; Groups"
date: 2009-01-07
forum: General Help
---

### Post by Bucky Ball on 2009-01-07
Hi all,

The title basically says it all. Trying to get the camera controls working with Kino and my DV camera and checked out PolicyKit to see if I could tweak anything in there. I couldn't change anything in there! Couldn't alter any authorisations. Same with Users and Groups. Can't 'unlock'. Maybe I have inadvertently changed a permission somewhere in my dabblings.

All ideas appreciated ...

---

### Post by namdung on 2009-01-07
I hope u haven't forgotten ur password.

In terminal
```
id
```
Check for **admin**, if it's not in the list then u r no longer an admin can no longer use the sudo command. 
Is this the first user created by Ubuntu (this will be admin by default)? Did u recently create another user with admin rights?

If admin, then paste output of 
```
sudo cat /etc/sudoers
```

---

### Post by Bucky Ball on 2009-01-07
?

No, haven't forgotten my password. Thanks anyway.

---

### Post by DarkRayne on 2009-01-09
I think I am having the same problem

here is what I get from that command 

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

and yes that user is an admin according to id

---

