---
title: "Selective ALT+TAB"
date: 2009-06-14
forum: Desktop Environments
---

### Post by beat on 2009-06-14
Just a quick question.
On Mac OS X there's a shortcut to switch between open windows of a certain program. For example if I have 3 open windows of firefox that shortcut would switch only between those 3 windows. Is there such a thing in Gnome?
I'm using the gnome-do docky so this is kinda handy. Also is there a way to make the Alt-tab list work like the one on Mac OS X, list open applications instead of open windows?
I'm using compiz I don't know if that makes any difference.

Thanks ;)

---

### Post by beat on 2009-06-15
Anyone? :(

---

### Post by techstop on 2009-06-16
You need to be running Compiz and have ccsm (sudo apt-get install compizconfig-settings-manager) installed.

Open ccsm and go to Static Application Switcher. Configure a binding for Next Window (Group) and Previous Window (Group).

I've just tested it and it flips between open windows of the same application.

---

### Post by beat on 2009-06-16
Thank you very much. That worked perfectly.
Now if there were a way to switch between groups (applications) that would be awesome. :P

---

### Post by techstop on 2009-06-16
> **beat said:**
> Thank you very much. That worked perfectly.
Now if there were a way to switch between groups (applications) that would be awesome. :P

Have a look at the "Group and Tab Windows" plugin. I haven't tried, but it looks like it might do what you want.

---

