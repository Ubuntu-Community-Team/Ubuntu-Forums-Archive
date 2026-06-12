---
title: "$PATH does not like me"
date: 2005-10-16
forum: Desktop Environments
---

### Post by dto on 2005-10-16
I've edited the $PATH variable in /etc/profile, ~/.bash_profile and ~/.profile to include /usr/local/jdk1.5.0_05/bin (where I put the Sun Java install), but the change is never recognized when I log in. 

For example, in /etc/profile, I changed it from:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
```
to:
```
PATH="/usr/local/jdk1.5.0_05/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
```
But I still get:
```
dave@moe:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11
```
Any idea of what I might be missing?

---

### Post by Leif on 2005-10-16
put it in your bashrc ?

---

### Post by seldenthuis on 2005-10-16
If it that happens in a gnome terminal, you mave have to check the 'Run command as a login shell' under Edit->Current Profile...->Title and Command. Otherwise the terminal won't load /etc/profile and /etc/bash.bashrc.

---

### Post by dto on 2005-10-16
[QUOTE=seldenthuis]If it that happens in a gnome terminal, you mave have to check the 'Run command as a login shell' under Edit->Current Profile...->Title and Command. Otherwise the terminal won't load /etc/profile and /etc/bash.bashrc.[/QUOTE]
Thanks for that!

---

