---
title: "Ubuntu user management"
date: 2005-05-22
forum: Desktop Environments
---

### Post by mherring on 2005-05-22
Am I the only one who is annoyed at the way Ubuntu sets up users?

Specifically, you start with a user account with some (but not all?) root powers, then you have to activate the root account.

It is (to me) counterintutive to be logged in, open something that needs root priveleges, and then enter your password instead of root.

Here' a real quirk:  You open the root terminal with your personal login password, but in a regular terminal you "su" to root using the ROOT passward.

Is there a way to set things up to work "Normally"---eg like every other Linux distro?

---

### Post by @jens on 2005-05-22
Hello

You can setup a "normal" root account and open a root shell via su:

$ sudo passwd root
password

Anyway, Ubuntu's root terminal still works with your *user password*, and a root-login to X is not allowed (well done, ubuntu!)  :smile: 

Regards,
@jens

---

### Post by angkor on 2005-05-22
[QUOTE=mherring]
Here' a real quirk:  You open the root terminal with your personal login password, but in a regular terminal you "su" to root using the ROOT passward.

Is there a way to set things up to work "Normally"---eg like every other Linux distro?[/QUOTE]

There's a difference between 'su' and 'sudo'. Ubuntu uses 'sudo' by default. You can enable root access and 'su' as described above. To me it isn't unintuitive at all since I used to have both in Debian as well. To open one program as root I've always used 'sudo'. I think its safer than starting a root session everytime you want to open one program as root.

---

### Post by Sam on 2005-05-22
[http://ubuntuguide.org/#usersadministration](http://ubuntuguide.org/#usersadministration)

---

