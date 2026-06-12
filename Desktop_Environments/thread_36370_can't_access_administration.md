---
title: "can't access administration"
date: 2005-05-23
forum: Desktop Environments
---

### Post by Infernal on 2005-05-23
i reinstalled ubuntu 5.0.4 and i am not possible to access any administration controls like users and groups, login screen setup, ... . When i open an administration tab, he processes it for 10 sec and then just stops, he doesn't asks me for a pass or anything.What do i need to do about this.


thx

---

### Post by pdk001 on 2005-05-23
"sudo" is to be admin in the consol mode

---

### Post by Behel on 2005-05-23
Are you in the list of sudoers also? Check your sudoers file...
*sudo visudo*

It should look something like mine:
[I]# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin	ALL=(ALL) ALL[/I]

Try to run from the terminal instead of from the desktop: 
*sudo network-admin*

Tell us if there is any error messages...

---

### Post by Burgundavia on 2005-05-24
See the quick intro to Sudo at

wiki.ubuntu.com/RootSudo

Corey

---

