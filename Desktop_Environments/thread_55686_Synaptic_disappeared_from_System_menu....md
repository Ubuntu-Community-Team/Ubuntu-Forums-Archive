---
title: "Synaptic disappeared from System menu..."
date: 2005-08-09
forum: Desktop Environments
---

### Post by FNM on 2005-08-09
Synaptic is no longer in the admin menu under System. How can I put it back there? Currently, the only way for me to launch Synaptic is to open a root terminal.

---

### Post by SKLP on 2005-08-09
Any ideas how it could have disappeared? Have you perhaps been using any menu editing software?

---

### Post by SKLP on 2005-08-09
Anyway if you want it fixed you can always add it to the menu with a menu editor, for example SMEG, search ubuntuforums for howtos.

---

### Post by FNM on 2005-08-09
[QUOTE=SKLP]Any ideas how it could have disappeared? Have you perhaps been using any menu editing software?[/QUOTE]

Yeah, I use Smeg to edit the applications menu, but it doesn't let you edit anything else, like Places, or System.

---

### Post by varunus on 2005-08-09
Open a terminal and cd over to /usr/share/control-center-2.0/capplets/

Do you see a synaptic.desktop file there?

If not, put the attached file there.  Make sure to rename it to synaptic.desktop instead of synaptic.desktop.txt.

---

### Post by FNM on 2005-08-09
[QUOTE=SKLP]Anyway if you want it fixed you can always add it to the menu with a menu editor, for example SMEG, search ubuntuforums for howtos.[/QUOTE]

I added Synaptic to my Applications/System Tools menu, but when I try launching it with the 'synaptic' command, I get an error saying I need to run the program as root. Do I need to use a specific run command for launching a program as root?

---

### Post by varunus on 2005-08-09
Use "gksudo synaptic" instead of synaptic, it'll bring up that box asking you for your password.

---

### Post by FNM on 2005-08-09
[QUOTE=varunus]Open a terminal and cd over to /usr/share/control-center-2.0/capplets/

Do you see a synaptic.desktop file there?

If not, put the attached file there.  Make sure to rename it to synaptic.desktop instead of synaptic.desktop.txt.[/QUOTE]

Yeah, it's there.

---

### Post by WAM on 2005-08-10
Hm... that's bizarre.

Just curious, is there an /etc/X11/sysconfig/synaptic.desktop ?

---

### Post by FNM on 2005-08-10
[QUOTE=WAM]Hm... that's bizarre.

Just curious, is there an /etc/X11/sysconfig/synaptic.desktop ?[/QUOTE]

Yeah, it's the only one in the folder.

---

### Post by hurinth on 2008-05-08
Hello, I am having a similar problem. Here:
-System>Administration>Synaptic is not present
-System>Administration>Software Sources is not present
-If I go to System>Preferences>Main Menu, I see those options unchecked
-If I check them, they uncheck by themselves 1 sec later
-I attached an error picture
-Regarding this post:

> **varunus said:**
> Open a terminal and cd over to /usr/share/control-center-2.0/capplets/

Do you see a synaptic.desktop file there?

If not, put the attached file there.  Make sure to rename it to synaptic.desktop instead of synaptic.desktop.txt.
The only thing under capplets is 'icons' folder
-And regarding this one:
> Just curious, is there an /etc/X11/sysconfig/synaptic.desktop ?
I can´t see 'sysconfig' under X11.
-I also can't set the priveleges of my user in System>Administration>Users and Groups

Please help I need Synaptic back and have no idea what to do

---

