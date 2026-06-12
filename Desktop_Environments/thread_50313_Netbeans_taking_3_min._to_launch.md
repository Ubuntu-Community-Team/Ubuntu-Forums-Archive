---
title: "Netbeans taking 3 min. to launch"
date: 2005-07-19
forum: Desktop Environments
---

### Post by mark465 on 2005-07-19
Netbeans appeared to install normally, running the installer binary from Sun.  Yet Netbeans is taking 3 minutes to launch its gui when run from the command line, and refuses to launch at all when launching from the Desktop icon.  My Kubuntu installation is on a Sony laptop.  Other programs seem to be running normally.  Any ideas?

---

### Post by holr on 2005-07-20
[QUOTE=mark465]Netbeans appeared to install normally, running the installer binary from Sun.  Yet Netbeans is taking 3 minutes to launch its gui when run from the command line, and refuses to launch at all when launching from the Desktop icon.  My Kubuntu installation is on a Sony laptop.  Other programs seem to be running normally.  Any ideas?[/QUOTE]

i have just installed this software myself, and certainly do not have to wait that long for it to load up. 

If it isn't loading from the desktop icon (which I presume was created by the installer) is it worth removing the whole program and trying again? are you getting any error messages in the terminal while the gui is loading?

---

### Post by mark465 on 2005-07-20
Netbeans is now acting right after I changed the permissions of the configuration files:

chmod a+w -R /home/<user>/.netbeans

I'm not sure why the permissions were tripping me up, though I was getting some error messages related to "read-only" permission files.

Thank you for the help!

Marc

---

