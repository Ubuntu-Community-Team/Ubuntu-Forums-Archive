---
title: "Restarting X"
date: 2006-09-14
forum: Desktop Environments
---

### Post by xhie on 2006-09-14
I need a script that will restart X that any user can run. 

I tried 
```

#!/bin/bash
/etc/init.d/gdm restart
```

I made the owner root and then suid on it with 
chmod u+s script name

This did not work. 

If its at all possable to make it restart without haveing to login again that would be great. I mean if a user name Mike were to run the script it would shutdown X, start X back up without asking for a password, and Mike would be logged in when its done restarting. 

Can anyone tell me how I can do this?

Thank you again.

---

### Post by aysiu on 2006-09-14
Can't any user restart X by just pressing Control-Alt-Backspace?

---

### Post by xhie on 2006-09-14
Yes but it takes you to the login screen, that is what I want to skip. 

Its a script that switches out my xorg.conf file and restarts X in order to rotate my screen on a tablet. It would be a whole lot easier if I didnt have to log in every time I want to rotate my screen.

---

### Post by aysiu on 2006-09-14
Ah... so this script restarts the X server without having to log out? That's cool.

I believe there's a way with the /etc/sudoers file to do this, but I don't know the exact syntax...

---

