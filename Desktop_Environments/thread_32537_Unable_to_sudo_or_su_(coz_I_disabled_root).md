---
title: "Unable to sudo or su (coz I disabled root)"
date: 2005-05-08
forum: Desktop Environments
---

### Post by msmales on 2005-05-08
Hi all,

I was unable to go to System -> Administration -> Networking because it asked me for a password.

But from the command line I can su as root and type network-admin to bring up the GUI.

I thought what if I do this (as root):

visudo

and I changed root to marty (my username), somehow I decided to change it back to root.

Also, I thought what if I disable root by typing (as found at bottom of page at [http://www.ubuntulinux.org/wiki/RootSudo):](http://www.ubuntulinux.org/wiki/RootSudo):)

sudo passwd -l root

Now I cannot access Networking via System -> Administration nor from the command line. From the command line, it says:

marty@earthquake:~$ su
Password:
su: Authentication failure
Sorry.
marty@earthquake:~$ sudo network-admin
marty is not in the sudoers file.  This incident will be reported.
marty@earthquake:~$

Any idea how I would access System -> Administration -> Networking? 

Thanks,

Marty

---

### Post by Gandalf on 2005-05-08
[QUOTE=msmales]Hi all,

I was unable to go to System -> Administration -> Networking because it asked me for a password.

But from the command line I can su as root and type network-admin to bring up the GUI.

I thought what if I do this (as root):

visudo

and I changed root to marty (my username), somehow I decided to change it back to root.

Also, I thought what if I disable root by typing (as found at bottom of page at [http://www.ubuntulinux.org/wiki/RootSudo):](http://www.ubuntulinux.org/wiki/RootSudo):)

sudo passwd -l root

Now I cannot access Networking via System -> Administration nor from the command line. From the command line, it says:

marty@earthquake:~$ su
Password:
su: Authentication failure
Sorry.
marty@earthquake:~$ sudo network-admin
marty is not in the sudoers file.  This incident will be reported.
marty@earthquake:~$

Any idea how I would access System -> Administration -> Networking? 

Thanks,

Marty[/QUOTE]
 OHHH!!!!! you disabled all super user access :D
[http://ubuntuguide.org/#gainrootwithoutlogin](http://ubuntuguide.org/#gainrootwithoutlogin) follow this

---

### Post by msmales on 2005-05-08
Thanks Gandalf,

That sorted out the problem.

I am able to change to root.

Now, how can I go to System -> Administration -> Networking and enter the correct password? I tried the root's password and my username's password but both do not work.

I prefer not to access Networking from the command line.

Thanks,
Marty

---

### Post by Gandalf on 2005-05-08
[QUOTE=msmales]Thanks Gandalf,

That sorted out the problem.

I am able to change to root.

Now, how can I go to System -> Administration -> Networking and enter the correct password? I tried the root's password and my username's password but both do not work.

I prefer not to access Networking from the command line.

Thanks,
Marty[/QUOTE]
 you have to re-enable sudo access to your user
type su
and then
EDITOR=gedit visudo

make it look like this
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

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL

```

---

### Post by msmales on 2005-05-08
Ah thank you, you are a real champion.

Although, I made one small change from your example (as there is no admin group, so I decided to use the adm group where my username is already part of the group):

# Members of the admin group may gain root privileges
%adm	ALL=(ALL) ALL

---

### Post by Gandalf on 2005-05-09
[QUOTE=msmales]Ah thank you, you are a real champion.

Although, I made one small change from your example (as there is no admin group, so I decided to use the adm group where my username is already part of the group):

# Members of the admin group may gain root privileges
%adm	ALL=(ALL) ALL[/QUOTE]
 well i'm happy to hear that :D

---

