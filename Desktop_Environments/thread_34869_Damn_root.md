---
title: "Damn root"
date: 2005-05-16
forum: Desktop Environments
---

### Post by stevanhe on 2005-05-16
Hi you all!

I read some topics about the sudo command and the problems with root,
during the installation of Ubuntu i wasn't asked to set any root password, is there the root login, and if it's like that what is the password like? How does "sudo" works? Why can't I use the "su" command?

Tnx for any answer you'll post...

Stevanhe (at my 1 installation of ubuntu... \\:D// )

---

### Post by jdong on 2005-05-16
There is no root login. Ubuntu decided to use 'sudo' instead, which gives an ordinary user the power to obtain administrator rights.


This is because Ubuntu is primarily targeted at desktops where there's a single user. Forcing him to remember 2 passwords only mean he'll choose weaker passwords for both users!


To run a program as root, type in "sudo program". Sudo then prompts for YOUR password (the one you log in with).

If you'd like a root shell for some reason, run "sudo su -" (yes, you need the dash).

---

### Post by shador on 2005-05-16
you can set a root password by typin "sudo passwd" ...i think.

Hey, the first time i've responded to a question! :D I'm so proud :)

---

### Post by bored2k on 2005-05-16
[QUOTE=shador]you can set a root password by typin "sudo passwd" ...i think.

Hey, the first time i've responded to a question! :D I'm so proud :)[/QUOTE]
 [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

Congrats . Keep up the good work ;)

---

### Post by stevanhe on 2005-05-19
tnx u all...

Now I got the super-user power!
May the Force be with me. And with you all.

See u!

---

### Post by poofyhairguy on 2005-05-19
I moved this because anyone who knows what su is (its root) doesn't belong in the beginner forums.

Pardon the mess made by new construction (aka new forum).

---

