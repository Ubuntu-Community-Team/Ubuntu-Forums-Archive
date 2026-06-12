---
title: "OpenSuse Gnome: Duplicate Accounts?"
date: 2009-05-13
forum: Desktop Environments
---

### Post by djoe on 2009-05-13
On Windows You Can Create A New User and Duplicate the Settings and Look.

Is there a way to do this on OpenSuse Gnome?

---

### Post by apmcd47 on 2009-05-14
I use KDE rather than gnome. With KDE there is a .kde directory in your home directory which holds all the settings. Once you have all the settings to your taste all you have to do is ```
tar cvf kde_settings.tar .kde
``` and then untar that file into the new user to duplicate them.
The question is what is the equivalent directory in gnome? Is it .gconf? If so, try ```
tar cvf gnome_settings.tar .gconf
``` in the model user account, copy gnome_settings.tar to the new account and run ```
tar xvf gnome_settings.tar
```as the new user. Remember to login with a terminal session rather than using the GUI otherwise you will overwrite the new settings with the original ones :-(

Andrew

---

