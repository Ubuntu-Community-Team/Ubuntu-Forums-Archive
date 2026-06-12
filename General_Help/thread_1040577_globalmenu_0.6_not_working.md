---
title: "globalmenu 0.6 not working"
date: 2009-01-15
forum: General Help
---

### Post by Ianprime0509 on 2009-01-15
I installed globalmenu 0.6, and added it to the panel, but only the application name is showing. I also created a .gnomerc file in Home with:

# Uncomment to load the GTK module
export GTK_MODULES=globalmenu-gnome

# Uncomment to tell the GTK module to open a Gtk
# TreeView for all menus in the application you start.
# export GNOMENU_FUN=1

# Uncomment to disable global menu.
export GNOMENU_DISABLED=0

# Uncomment to print a lot of debugging messages
# export GNOMENU_VERBOSE=1

# Uncomment to save the debugging messages to the given file.
# export GNOMENU_LOG_FILE=/tmp/gnomenu.log

# Uncomment to disable the plugin for specific programs.
# export GTK_MENUBAR_NO_MAC="fast-user-switch-applet"


I also logged out and back in, and then opened up a file browser, but it didn't work on that or Terminal(or anything else). Do I have to install something else(or patch GTK)?

---

### Post by Ianprime0509 on 2009-01-16
Bump because I'm having a lot of trouble with this.

EDIT: I also tried compiling 7.2 from source, but it doesn't show up in the "add to panel" menu.

---

### Post by Freddy on 2009-01-23
You need to comment.
```
# Uncomment to disable global menu.
export GNOMENU_DISABLED=0
```
It should be.
```
# Uncomment to disable global menu.
# export GNOMENU_DISABLED=0
```

---

