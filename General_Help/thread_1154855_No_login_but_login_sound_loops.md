---
title: "No login but login sound loops"
date: 2009-05-10
forum: General Help
---

### Post by Dracu@l on 2009-05-10
Hi, this morning I started up my computer, everything seemed fine in boot loader and stuff. 
but when the login screen was supposed to show up, i hear the ubuntu startup sound and then the mouse changes to a "thinking/working" icon, then screen flashes once and it plays the startup sound again (pointer normal, then goes to thinking/working). this process loops in the infinite, it is possible to press ctrl+alt+F1 and get the command line. and even then the startup sound loops.
please help
 
: + when i ran the "sudo reboot" from terminal it said "pidfile not found"

---

### Post by geirha on 2009-05-10
Something is wrong with gdm then it seems. Log in at the console (ctrl+alt+f1) and stop gdm ```
sudo /etc/init.d/gdm stop
```

Then look at gdm's log file and see if you can find any error messages
```
less /var/log/gdm/\:0.log
```

---

### Post by Dracu@l on 2009-05-10
Nope, no errror, only default setting. no error messages at all, the only thing on the page saying anything about errors was the markers.

---

### Post by vahnx on 2009-05-10
Sounds maybe like you have a login script that is executing gdm after it plays the login sound, possibly after all your services. It also seems like it's set to autologin too. I forget how, but there's a place where you can put scripts that run after everything else, check there. Also see if auto login is enabled.

---

### Post by Dracu@l on 2009-05-10
well auto login was not enabled last time i logged in. so that should not be on. 
how do i see what scripts are running?
 
Or maybe i should just do it easy and uninstall edubuntu from terminal, how do I do that  ? ... (im a n00b)

---

### Post by Dracu@l on 2009-05-10
did not work to run 
apt-get remove edubuntu-desktop
still same login screen

---

