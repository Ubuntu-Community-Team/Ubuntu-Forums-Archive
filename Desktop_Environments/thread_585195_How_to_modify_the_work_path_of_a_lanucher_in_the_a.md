---
title: "How to modify the work path of a lanucher in the applications menu?"
date: 2007-10-21
forum: Desktop Environments
---

### Post by cwmccabe on 2007-10-21
How can I modify the "work path" of an application ([ZDT Language Learner]("http://zdt.sourceforge.net/")) that is started from the Applications menu?  When I start the app by double-clicking on its icon in Nautilus, it works as normal.  But when I start it from the launcher I placed in the Applications menu it won't work because it can't reference files needed to start up.  Someone else had (and [solved]("http://www.chinese-forums.com/showpost.php?p=110547&postcount=3")) this same problem in KDE, but I can't figure out how to do it in Gnome.  It seems that the launchers in KDE allow you to modify the work path of the application being launched.  In Gnome?  Can anyone help?

---

### Post by realillusions on 2007-10-21
If I understand what you're asking correctly...

Right click the main menu and hit "Edit Main Menu" then navigate to the item you want to edit. Right click it, and select "Properties". The Launcher Properties dialog will open, and you can edit the command in the appropriate blank.

---

### Post by cwmccabe on 2007-10-23
Problem solved.  It ended up that I didn't need to modify the work path (although that too probably would have worked).  Instead, in the ZDT preferences, there is an option to change the location of the database file (user.script).  I rerouted that to the file's location, and now it's working correctly when launched from the applications menu.

---

