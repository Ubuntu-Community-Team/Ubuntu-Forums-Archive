---
title: "[SOLVED] slightly urgent user permissions problem"
date: 2008-12-20
forum: General Help
---

### Post by Neonfire on 2008-12-20
I've made what seems to be a stupid mistake, I've migrated from windows and it looks like I've learnt just enough to really mess it up. After using the included installer to install a a game ([http://www.planeshift.it/download.html](http://www.planeshift.it/download.html), run with root access) I've managed to mess up my account to such an extent that although it accepts my login name and password the main gnome interface does not load, leaving me with the default background. Right click does not work. I have tried getting to the files via root access from a terminal in restore mode but I don't seem to be able to get to them from here either, otherwise I'd be tempted to back them up and do a clean install.

Within the installer i chose the option to install to all users on the system and into a folder in my home directory (/home/$USER/program files/planeshift/), i think this is what went wrong. On booting I get the following error messages. Is there anything i can do to fix the account?

"User's $HOME/.drmc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not be writable by others."

"could not update ICEauthority file /home/david/.ICEauthority".

"There is a problem with the configuration server
(/usl/lib/libgconf2-4/gconf/-sanity-check 2 2 exited with status 256"

"cannot create the directory /home/david/.gnome2/sharefonts
This is needed to allow changeing the mouse pointer theme"

"There was an error starting up the screensaver:
Failed to change to directory '/home/david' (permission denied)
screensaver functionality will not work this session"

Thanks for any help.

---

### Post by sisco311 on 2008-12-20
drs305 has a detailed tutorial here:

[http://ubuntuforums.org/showthread.php?t=976610]("http://ubuntuforums.org/showthread.php?t=976610")

---

### Post by albinootje on 2008-12-20
> **Neonfire said:**
> 
"There was an error starting up the screensaver:
Failed to change to directory '/home/david' (permission denied)
screensaver functionality will not work this session"

1) Boot in "recovery mode"
2) Choose "drop to root shell"
3) type in : chown -R david:david /home/david
4) type in : init 2

---

### Post by Neonfire on 2008-12-20
problem solved, thanks!

---

### Post by sisco311 on 2008-12-20
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

Marking threads as [SOLVED], after a solution has been found will help
others to find an expedient solution for their own issues.

---

