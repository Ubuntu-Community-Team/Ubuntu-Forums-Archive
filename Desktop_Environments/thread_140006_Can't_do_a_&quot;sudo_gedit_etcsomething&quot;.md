---
title: "Can't do a &quot;sudo gedit /etc/something&quot;"
date: 2006-03-05
forum: Desktop Environments
---

### Post by SmartWarthog on 2006-03-05
After I used pppoeconf to set my internet connection up, I can't do a "sudo gedit" in the terminal anymore. I just wait a minute or two and then get an enormous error message, which I'm posting here:

```

** (gedit:8915): CRITICAL **: gedit_mdi_set_state: assertion `GEDIT_IS_MDI (mdi) ' failed

(gedit:8915): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in  cast to `BonoboMDI'

** (gedit:8915): CRITICAL **: bonobo_mdi_get_active_child: assertion `BONOBO_IS_ MDI (mdi)' failed

(gedit:8915): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in  cast to `BonoboMDI'

** (gedit:8915): CRITICAL **: bonobo_mdi_get_active_window: assertion `BONOBO_IS _MDI (mdi)' failed

** (gedit:8915): CRITICAL **: gedit_utils_set_status: assertion `BONOBO_IS_WINDO W (win)' failed

** (gedit:8915): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

** (gedit:8915): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:8915): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_pre fs_manager->gconf_client != NULL' failed

** (gedit:8915): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_pref s_manager->gconf_client != NULL' failed

(gedit:8915): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in  cast to `GObject'

(gedit:8915): GLib-GObject-WARNING **: instance of invalid non-instantiatable ty pe `(null)'

(gedit:8915): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TY PE_CHECK_INSTANCE (instance)' failed

```

I tried to do a "sudo nautilus" and open the file from there, but it doesn't work either... it says "Opening file..." but nothing happens.

---

### Post by Zeroangel on 2006-03-05
Have you tried "gksudo nautilus" ?

---

### Post by IAmAI on 2006-03-05
I hope the author of this thread doesn't mind me butting in. I am having problems with *gksudo*. If I want to edit a file as root using *gedit* I can use [COLOR="DimGray"][FONT="Courier New"]sudo [-b] gedit[/FONT][/COLOR], and that works fine with no repercussion, even though I have read that it quite acutely adviced that *gksudo* is used, rather than *sudo* for GUI applications. I then recently installed and ran *kate* (yes, on Gnome) using *sudo* to my expense; it caused my login to fail due to the ownership of *~/.ICEauthority* being set to *root*, as I had been warned, but forgot.

I would happily use *gksudo*, if it worked! If I try say, [COLOR="DimGray"][FONT="Courier New"]gksudo gedit /etc/fstab[/FONT][/COLOR], after entering a correct password, I get the following error message:

```

$ gksudo gedit /etc/fstab
(gedit:10671): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified
are supported and host-based authentication failed.

```
*gedit* will still load, with a blank file claiming to be of the pathname *~/'/etc/fstab'*. Very strange. Does anyone know what is causing this and how to fix it so I can use *gksudo* properly?

**Edit:**
It sure helps to search! I have find the problem with *gksudo* and the solution ([here]("http://ubuntuforums.org/showthread.php?t=132553&highlight=gksudo+ged")). Unlike *sudo*, the command requires quoting, like this:

```

gksudo 'gedit /etc/fstab'

```
Despite the error message I described earlier I was able to edit *fstab* using *gedit*.

---

