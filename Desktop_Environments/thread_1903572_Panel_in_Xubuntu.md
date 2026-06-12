---
title: "Panel in Xubuntu"
date: 2012-01-02
forum: Desktop Environments
---

### Post by jord1981 on 2012-01-02
I recently switched my Ubuntu install to Xubuntu.  Panel was not loading on startup, so I added it as an application in the Application Autostart list under Session and Startup.

Thereafter, about 5 instances of panel launched on boot.  I removed it from the autostart list but now I continue to get many instances on each boot, the number seems to be growing.

Does anyone know how I can fix this and get neither 0 instances nor 10, but just 1?

Many thanks in advance.

---

### Post by Paddy Landau on 2012-01-03
The only thing I can think of is to entirely reset your settings.

I don't know specifically where the settings are held for the panel, so in your place I would back up my data; completely empty my home folder of all hidden folders and files (i.e. folders and files beginning with "."); log out; log in again.

If you still get a problem, I would suspect something got corrupted during the installation.

---

### Post by mike555 on 2012-01-04
better to do a clean install of Xubuntu (not into Ubuntu)and copy only certain things from your /home folder (not old .settings )

---

### Post by andrewc on 2012-01-04
In my exprience XFCE setttings can occasionally get corrupted. Log in under another window manager (or at the recovery console) and delete or rename: 
```
~./cache/xfce4 (if it exists) 
~/.cache/Thunar 
~/.cache/sessions 
~/.config/xfce4 
~/.config/Thunar 

```

---

