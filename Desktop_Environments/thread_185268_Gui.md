---
title: "Gui"
date: 2006-05-31
forum: Desktop Environments
---

### Post by cleentrax on 2006-05-31
I would have expected to find a GUI User Management tool in System -> Administration. But I don't see one.

Is there a Dapper GUI tool for creating and managing user accounts? Or must I resort to the command line?

[EDIT] Solved. I re-installed gnome-system-tools, and got lots of additional menu options.

---

### Post by rjwood on 2006-05-31
[quote=cleentrax]I would have expected to find a GUI User Management tool in System -> Administration. But I don't see one.

Is there a Dapper GUI tool for creating and managing user accounts? Or must I resort to the command line?[/quote]

Mine is there. system>administration>users and groups.

---

### Post by cleentrax on 2006-05-31
My "Administration" menu ends with Update Manager. How do I get "Users and Groups"?

---

### Post by disturbed1 on 2006-05-31
gksu users-admin

It's under System - Administration.

---

### Post by cleentrax on 2006-05-31
It's NOT under System/Administration on my machine... and that command did nothing. How do I rebuild my menus?

---

### Post by henriquemaia on 2006-05-31
This is how my administration menu looks like.

---

### Post by thasheep on 2006-05-31
Cleentrax, are you in the admin group? ie, if you type 'groups' into a terminal, does 'admin' show up?
Also, do you have the package gnome-system-tools? If not, get it 'sudo apt-get install gnome-system-tools' if you do have it then 'sudo apt-get --reinstall install gnome-system-tools'

---

