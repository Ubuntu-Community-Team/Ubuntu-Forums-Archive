---
title: "sudo not working (newbie help)"
date: 2006-02-18
forum: Desktop Environments
---

### Post by NZJoe on 2006-02-18
Hi,  I've just got Ubuntu 5.10 installed and dual booting with WinXP.  during install, I created a root password and 1 user.  I can log on with the username and password.  However, sudo does not work. It does ask me for the password (I use the user password as the wiki says).  In the terminal I can switch user to root OK and run any commands as root.  Does anyone know why sudo is not working?  Thanks.  Joe

---

### Post by Turtle.net on 2006-02-18
If you have a passwd for root, then the password for sudo should be your root password (I think)

Hope this helps :)

---

### Post by rfruth on 2006-02-18
So if sudo doesn't work how do you log in as root - And when sudo fails whats the error message ? :confused:

---

### Post by NZJoe on 2006-02-18
su root (which then prompts for root password)

This lets we do whatever I want like play with permissions etc.  If I try to do is as a user with sudo it doesn't work.

---

### Post by NZJoe on 2006-02-18
...and there is no error message, it just has no effect

---

### Post by bikeman on 2006-02-19
Question - did you run the install in expert mode?  It seems that when using the expert mode, it does not add your user to the sudo list, so your username does not have permissions.  That happened to me, and I had the same symptoms - no error message, but the command did not work either.  Here is how you add your username to the sudoer list:

Type (in the terminal):
export EDITOR=gedit && sudo visudo

When the file opens, add the following line at the end of file (use your username instead of system_username):
system_username	ALL=(ALL) ALL

Save the edited file (keep the same name and do not add an extension!).

Close and restart terminal, it should work.  If not, reboot then try to sudo again.

---

### Post by Treebeard on 2006-02-19
[QUOTE=NZJoe]su root (which then prompts for root password)

This lets we do whatever I want like play with permissions etc.  If I try to do is as a user with sudo it doesn't work.[/QUOTE]
You can not become root with "su", because your root password is locked ([https://wiki.ubuntu.com/RootSudo)](https://wiki.ubuntu.com/RootSudo)).

However you can get a root terminal with ```
$ sudo -s
```

---

### Post by NZJoe on 2006-02-19
Thanks Bikeman, that was it.

Treebeard, I can su root, I set the password during the install.  It works

---

