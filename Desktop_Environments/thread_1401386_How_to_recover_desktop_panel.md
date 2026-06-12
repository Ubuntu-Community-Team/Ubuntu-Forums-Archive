---
title: "How to recover desktop panel?"
date: 2010-02-08
forum: Desktop Environments
---

### Post by gdesilva on 2010-02-08
I accidentally deleted the desktop panel which had the bluetooth, hplip icons. Can someone please tell me how I could add them back on?

Thanks

---

### Post by azertyh on 2010-02-08
[I]hi, 
type on terminal gnome-panel --restart [/I]

---

### Post by gdesilva on 2010-02-08
The only options I have are;

Unknown option -restart
Run 'gnome-panel --help' to see a full list of available command line options.
$ gnome-panel -h
Usage:
  gnome-panel [OPTION...] 

Help Options:
  -h, --help                     Show help options
  --help-all                     Show all help options
  --help-gtk                     Show GTK+ Options
  --help-bonobo-activation       Show Bonobo Activation options
  --help-gnome                   Show GNOME options
  --help-gnome-session           Show session management options

Application Options:
  --replace                      Replace a currently running panel
  --display=DISPLAY              X display to use


Any further suggestions? Tnxs

---

### Post by sm_here on 2010-02-08
how did you delete it

---

### Post by gdesilva on 2010-02-08
Right mouse click and 'Delete this Panel'....

The problem is now hplip, sound card settings and bluetooth applet icons are no longer visible althouth they still activated on 'Startup Applications'.

---

### Post by semi_fiction on 2010-02-08
> **gdesilva said:**
> Unknown option -restart


Well first of all it should be --restart not -restart...

---

### Post by gdesilva on 2010-02-08
Sorry, that was a typo. I tried both variants without any luck.

---

### Post by sm_here on 2010-02-08
Right-click on the already existing panel(top one) and select 'New Panel', you will get a new panel. Right-click on this and select 'Add To Panel'; you will get a list of all that you can have on a panel, select whichever you want. 
Do let me know if you are able to get it back the way it was.

---

### Post by gdesilva on 2010-02-08
> **sm_here said:**
> Right-click on the already existing panel(top one) and select 'New Panel', you will get a new panel. Right-click on this and select 'Add To Panel'; you will get a list of all that you can have on a panel, select whichever you want. 
Do let me know if you are able to get it back the way it was.


Hi, the problem is the items I deleted do not appear on the list. However, I tried to add the items (bluetooth applet, hp-systray) manually using Custom Application Launcher but the icons are still not visible - the processes appear to be running. 

Thanks.

---

### Post by sm_here on 2010-02-08
Restart the system and try again.

---

### Post by sm_here on 2010-02-08
did you try

---

### Post by gdesilva on 2010-02-08
Yes, many times. Re-installed hplip still the hplip icon and others not visible.

---

### Post by mcoleman44 on 2010-02-08
Open synaptic package manager and search for libpanel-applet2-0, and Gnome-Panel.
Mark them for re-instillation. I think.

---

### Post by mcoleman44 on 2010-02-08
And Gnome-applets, my bad.

---

### Post by gdesilva on 2010-02-08
Thanks for the hint but did not make much of difference. hplip program comes up with an error message 'no system tray was found on this system'.

---

### Post by gdesilva on 2010-02-08
Thanks everyone for suggestions...the solution was to add the 'Notification Area' to the panel. Someone else had the same issue and the solution was already there....should have searched the forum more....you live and learn!

---

