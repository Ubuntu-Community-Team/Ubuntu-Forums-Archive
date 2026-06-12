---
title: "can't log-in"
date: 2009-01-06
forum: General Help
---

### Post by addis123 on 2009-01-06
i try longing in to my "Ubuntu studio" but i keep getting this message
 
[SIZE="3"]
"The GNOME session manager was unable to lock the file '/home/addis123/.ICEauthorty.' Please report this as a GNOME bug. Sometimes this error may occur if the files directory is unwritable, you could try logging in via the failsafe session and ensuring that it is."[/SIZE] 

i did try to login using "failsafe GNOME" AND "failsafe Terminal" i couldn't get to the file that it keep saying "locked" please please help me.

---

### Post by bodhi.zazen on 2009-01-06
Boot to recovery mode.

Output of 

```
ls -la $HOME | grep .ICE
```

Edit : Moved to General Help

---

### Post by addis123 on 2009-01-06
thank you so much i'll give it a shot

---

### Post by bodhi.zazen on 2009-01-06
It is probably a permissions problem

Most likely (from recovery mode) you can simple

```
chown user.user /home/user/.ICEauthority
chmod 600 /home/user/.ICEauthority
```

Where "user" = you log in name

Then reboot

This most likely happened because you were running a graphical application as root (just a guess).

If running a graphical application as root, use gksu

---

