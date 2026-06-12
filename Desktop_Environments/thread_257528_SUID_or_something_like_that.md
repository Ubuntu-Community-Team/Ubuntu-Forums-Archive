---
title: "SUID or something like that"
date: 2006-09-14
forum: Desktop Environments
---

### Post by xhie on 2006-09-14
I have a script that switches out my xorg.conf file whenever I want my screen to rotate (its a tablet). because its accessing the /etc/X11 directory it needs to have root privileges. I don't want to change the permissions on /etc/X11 or on xorg.conf. 

How do I give this script the privileges to do this so any user could run the script and it would work?

The script works just fine when I run it with sudo, but I don't want to have to enter a password every time I use it because it will be a little icon at the top of my screen. 

Thanks for any help.

---

### Post by lamego on 2006-09-14
Change the script owner to root.
Set the setuid bit on it with:
```
chmod u+s script
```
This will make the script to run as root no matter the user which is calling it.

---

### Post by xhie on 2006-09-14
thank you!

---

