---
title: "configuring panels on gnome desktop"
date: 2010-12-25
forum: Desktop Environments
---

### Post by MakOwner on 2010-12-25
I want to duplicate the panel settings from one machine to another - which configuration files need to be copied between machines to duplicate the desktop panel positions and applet loading?

---

### Post by karthick87 on 2010-12-25
AFAIK you cant do that i guess..You have to install all the applets and you have to add it manually in other system..

---

### Post by MakOwner on 2010-12-25
> **karthick87 said:**
> AFAIK you cant do that i guess..You have to install all the applets and you have to add it manually in other system..

Surely the position and geometry of the panels are stored somewhere, are they not?

---

### Post by aceofspades686 on 2010-12-25
I haven't ever done this specifically, so take this advice with a grain of salt, but assuming that you have all the same applications installed you should be able to copy the (hidden) Gnome folders in your home directory.
```

~/.gconf
~/.gconfd
~/.gnome2
~/.gnome2_private
```
I believe that's all of them, hopefully someone will correct me if I'm wrong.

---

### Post by Heithy on 2010-12-25
since this thread is about panels, i think it's somewhat appropriate to ask this question here...

is it possible to have a panel operate differently on different workspaces? ie; can i have the panel auto hide on workspace2 but not the others?

thanks in advance.

---

