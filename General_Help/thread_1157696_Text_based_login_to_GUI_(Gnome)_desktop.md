---
title: "Text based login to GUI (Gnome) desktop"
date: 2009-05-13
forum: General Help
---

### Post by tgeer43 on 2009-05-13
Sounds easy but I can't find an answer on this.
I don't use a startup screen and prefer to watch everything load. I don't need or want a graphical login screen either and would prefer to login right from the command line but then have it finish booting and display my normal gnome desktop without me having to do or type anything else.

Is this possible?

Thanks in advance.

Tom

---

### Post by geraldvillorente on 2009-05-13
I dont think if this is possible in Jaunty Jackalope...but in earlier version of Ubuntu this is enabled....

---

### Post by stathol on 2009-05-13
I think all you need to do is disable GDM (Gnome Display Manager). I'm pretty sure these instructions are still valid:

[Ubuntu Linux stop / disable GNOME GUI ~ X.org](http://www.cyberciti.biz/faq/prevent-xorg-from-starting-in-linux/)

You might want to investigate virtual terminals, too. Like most distros, Ubuntu creates several of these by default. Probably one of them is already configured to catch all the system messages during boot up. If your objective is simply to be able to see the boot output, switching over to one of the virtual consoles before logging in via GDM would be a less "invasive" solution.

---

