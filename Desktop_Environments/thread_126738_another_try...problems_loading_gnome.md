---
title: "another try...problems loading gnome"
date: 2006-02-07
forum: Desktop Environments
---

### Post by lucaflea on 2006-02-07
hi. 
i hope, this time, someone could answer my questions...

i can't log in gnome anymore. when it (graphically) loads window manager Metacity, it stalls (stops...) and then it returns to the splash screen.

i tried to uninstall gnome and gdm... but no way.

please, someone...

---

### Post by kaamos on 2006-02-07
Just a thought: login to the console (ctrl+alt+f1) and
```

cd ~
mkdir gnome_backups

```
and then
```

mv .gconf gnome_backups/; mv .gconfd gnome_backups/; mv .gnome gnome_backups/; mv .gnome2 gnome_backups/; mv .gnome2_private gnome_backups/

```
Then try again. If it does not work, you can revert the changes by moving the folders from gnome_backups back to you home folder.

---

### Post by lucaflea on 2006-02-07
thanx, i will try....

---

### Post by lucaflea on 2006-02-07
it works...great! but now??? do i have my "new" ubuntu box working? or is it a temporarely solution?

luca

---

### Post by tagg3rx on 2006-02-07
you just moved your gnome config files to a temp dir so new working ones would be created.

I would say its a perm fix and if you have no need for them (which i doubt you do) you can delete the gnome_backups folder in your home folder.

---

### Post by lucaflea on 2006-02-08
Great!!

a question... today, loggin' in, my pppoe didn't automatically start (i configured that way...).why? and, yesterday loggin out the log out screen was "without" buttons so i couldn't chose anything but turning off my pc...

luca

---

