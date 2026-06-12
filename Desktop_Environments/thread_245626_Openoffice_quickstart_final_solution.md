---
title: "Openoffice quickstart: final solution"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Cobra78 on 2006-08-28
Hallo.

First i want apologyze for my terrible english, but i've found the final solution for people thath have problem in eablinq openoffice quickstart.

Maybe this is not the most elegant way, but it works.

Create a new user, is not important the name, login with the new user, open openoffice end enable the quickstart with the menu.

Logout then login with the new user, and verify thath quickstart work, if yes logout and login as your normal user.

Now open a terminal and do

```

sudo cp /home/newuser/.config/autostart/ooqstart.desktop /home/youruser/.config/autostart/ooqstart.desktop

```

Maybe you need to add to the session start 

```

ooffice -quickstart -nologo -nodefault

``` 
Now logout then login with your normal user, and magically you see the openoffice quickkstart in system tray, and is persistent.

If it works you can delete the new user

Enjoy :D

---

### Post by kerry_s on 2006-08-28
you could have just installed "openoffice.org-gnome", then open OO and go to the settings>memory and check the box at the bottom for quick start.

---

### Post by Cobra78 on 2006-08-28
> **kerry_s said:**
> you could have just installed "openoffice.org-gnome", then open OO and go to the settings>memory and check the box at the bottom for quick start.

You don't think thath if i searched, and found, this sistem, is because the standard way don't worked forme?

Search the forum and you will find thath other people have the same problem, probably the cause is a configuration file from another installation, example upgrade breezy - > dapper, thath cause conflicts :P

---

### Post by petersjm on 2006-08-28
The built-in quickstarter works for me, but nice guide for anyone it doesn't work for. *MY* only problem is hiding the tray icon on start-up: I like to open OO.o from the panel and don't want the tray icon there. Anyone know a way to hide it?

---

