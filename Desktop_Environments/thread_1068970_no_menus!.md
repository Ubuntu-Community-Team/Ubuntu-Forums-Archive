---
title: "no menus!"
date: 2009-02-13
forum: Desktop Environments
---

### Post by profadour on 2009-02-13
I am using Intrepid on a Compaq 2710p laptop.  I have multiple user accounts, and up till recently had no problems.  A few days ago, i started having trouble with the administrative user account - the GNOME menus no longer load.  The desktop itself loads, but no menus, no panel, no way to access programs.  My standard account is working just fine, but i also cannot install new programs or get updates.
Any assistance is appreciated.
Thanks, profadour.

---

### Post by UbuntuNerd on 2009-02-13
what happens if you press alt+f2

---

### Post by profadour on 2009-02-13
Well, when i press Alt+F2, i get the "Run Application" box, which lists everything i would get from the Applications menu.

---

### Post by UbuntuNerd on 2009-02-13
hit the alt+f2 and type this commands in it hit run and see if you get your panels back

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by prshah on 2009-02-13
> **profadour said:**
> i get the "Run Application" box, 

Launch a terminal from the "Run" box```
gnome-terminal
``` and then give the command to load the panels```
gnome-panel
``` If you don't get your panels back, paste back any error messages received in the terminal; otherwise, close the terminal (The panels will disappear again), and this time, run the gnome-panel command from the "Run" box. Logout and login again, and everything should be a-OK.

---

### Post by profadour on 2009-02-14
Tried these commands, did not get the panels back.

> **UbuntuNerd said:**
> hit the alt+f2 and type this commands in it hit run and see if you get your panels back

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by profadour on 2009-02-14
Tried this.  Got the following output:
user@user-laptop:~$ gnome-panel
A panel is already running.

Odd.  And i still can't see the panels or menus...
Urgh.

> **prshah said:**
> Launch a terminal from the "Run" box```
gnome-terminal
``` and then give the command to load the panels```
gnome-panel
``` If you don't get your panels back, paste back any error messages received in the terminal; otherwise, close the terminal (The panels will disappear again), and this time, run the gnome-panel command from the "Run" box. Logout and login again, and everything should be a-OK.

---

