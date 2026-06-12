---
title: "Where is root access/user info under 8.10"
date: 2008-11-05
forum: Desktop Environments
---

### Post by socngill on 2008-11-05
I am trying to amend the settings so I can access all parts of my system.  In 8.04 I simply went to settings and then users, but that no longer exists.  I have no root option under terminal and also can't open any files or folders as root.

I have found the following: advanced - login manager - Users.  But the amended list is entitled "Excluded Users.  I don't want to exclude anything, I want to enable it all???

Any help would be greatly appreciated!

---

### Post by Coreigh on 2008-11-05
Issuing commands as privileged user (root) in the terminal is accomplished by typing sudo ahead of the command

for example to install a package:```
sudo apt-get install a-new-package
```

you are prompted for your password, *your* password not root's. and the command executes. If you are issuing several commands you are not asked for a password again for a period of time (15 min. I think), but you have to type sudo before each command.

It is a safer way to administer a computer and once you get used to the concept it is not cumbersome or annoying.

---

### Post by at165db on 2008-11-05
If you REALLY need root, because you are doing a lot of privelaged thing at once, you can always run this first:
```
sudo bash
```

But do yourself a favor, don't leave it open!

---

### Post by Coreigh on 2008-11-05
I think ```
sudo su
``` is similar to sudo bash. But that is dangerous. There is no net or fall-back if you make a mistake.

---

### Post by overdrank on 2008-11-05
The forums policy on root access.
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
Thread closed.

---

