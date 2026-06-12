---
title: "termanal password problem"
date: 2010-05-08
forum: Desktop Environments
---

### Post by sundays211 on 2010-05-08
hi.
my password doesn't work to enter super user mode in the terminal.
this password works for all other administartive uses in and out of the terminal, just not for entering super user mode.
any ideas what the problem could be?

---

### Post by nikefalcon on 2010-05-08
Do you mean sudo and su won´t accept your password??
Please elaborate.

---

### Post by MooPi on 2010-05-08
your password will not show up as you type it. Is that the problem?

---

### Post by sundays211 on 2010-05-08
I mean when i enter the "su" command into the termanal, and I enter my pasword (same as my login password, right?) it says "su: authentication failure". my password works in all other situations.

---

### Post by martijntje on 2010-05-08
Of course. If you use su, you are actually trying to log in to the root account and I highly doubt that account has the same password as yours.

If you want to open a root shell (which is rarely necessary) you can just type either 'sudo su', 'sudo bash' or something similar.

---

### Post by nikefalcon on 2010-05-08
If you want to run a command as root just use sudo followed by the command. 
[sudo] will ask you for your parrword. If you wan to run several commans as root, then try sudo bash, or sudo su. Alternately you could press Alt+F2 and enter
 "gksudo gnome-terminal" and run.
If you regularly need to use the root terminal then you might want to edit your gnome menu on the panel and check the box next to "Root Terminal" under System tools.

Mark this thread as solved.

---

### Post by aysiu on 2010-05-08
```
sudo -i
``` will give you a persistent root prompt.

For more details, see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sundays211 on 2010-05-08
sudo su works. my root pasword should be the same as my normal password as it was the only password I entered when i installed ubuntu. i have no idea why just su doesnt work though.

---

### Post by 3rdalbum on 2010-05-08
> **sundays211 said:**
> sudo su works. my root pasword should be the same as my normal password as it was the only password I entered when i installed ubuntu. i have no idea why just su doesnt work though.

Su prompts you for the root password. Your sudo password is different to the root password (which is disabled in Ubuntu).

You can 'su' to other users, but not to root, because there's no root password.

---

