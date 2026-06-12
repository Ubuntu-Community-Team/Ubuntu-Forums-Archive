---
title: "help...can't login!!!"
date: 2006-08-30
forum: Desktop Environments
---

### Post by harty83 on 2006-08-30
I came home today to my computer locked up.  So I had to do a hard reset.  It came up with my kdm login screen (which is not suppose to happen because I have auto login set).  I tried to log in, it shows the background of my desktop for a second then returns to the kdm login screen.  Both gdm and kdm does this.  I've tried the following to no avail:

Tried KDM and GDM 
Tried updating my system to all the latest updates
Tried "chown -r alan.alan /home/alan"

And nothing works.  I can't login using failsafe-gnome or failsafe-terminal.  I can login by pressing ctrl-alt-f1.  

Any suggestions?  I'm in the process of backing things up (a real pain in the ***) in case I have to resort to a complete restore.  But I would really like to avoid that.

Thanks!
Alan

---

### Post by tatimmer on 2006-08-30
I got into a problem with Mandrake 10.1 once where I could not login.  I ended up booting into safe mode and resetting the permissions (chmod) on my home directory /home/tom which has somehow changed to that I did not have read/write access.

---

### Post by mlind on 2006-08-30
Can you find anything related to this problem from  ~/.xsession-errors file?

Log into one of the tty terminals (Ctrl+Alt+F1) and type
```

less ~/.xsession-errors

```
There's probably a lot of output, so tailing the file might be easier.

---

### Post by harty83 on 2006-08-30
>  I got into a problem with Mandrake 10.1 once where I could not login. I ended up booting into safe mode and resetting the permissions (chmod) on my home directory /home/tom which has somehow changed to that I did not have read/write access.

That did it!!  Thanks!  I'll remember that.

---

### Post by mlind on 2006-08-30
This has happened to me when I (for reasons unknown..) executed *startx* using sudo.. As a result root was owner of the ~/.Xauthority file and result was pretty much the same.

---

