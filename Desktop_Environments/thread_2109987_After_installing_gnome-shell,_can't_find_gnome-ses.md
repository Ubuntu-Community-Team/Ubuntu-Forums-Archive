---
title: "After installing gnome-shell, can't find gnome-session-preferences"
date: 2013-01-29
forum: Desktop Environments
---

### Post by kalaka on 2013-01-29
Hi everyone,

My setup is:
Release 12.04 (precise) 32-bit
Kernel Linux 3.2.0-36-generic-pae
GNOME 3.4.2

I'm using Gnome-shell instead of unity, I'm guessing that could be the cause of my problem.
My problem is I can't find (or figure out how to install) Startup Application Preferences (aka gnome-session-preferences) and therefore can't edit my startup programs through a GUI, any suggestions?

Any help is much appreciated! :)

---

### Post by iMac71 on 2013-01-29
you might follow these steps:

[LIST=1]
[*]press ALT+F2
[*]type```
gnome-session-properties
```
[*]click the "Add" button
[*]in the resulting dialog box type the name and the command of each application you wish to add.
[/LIST]

---

### Post by kalaka on 2013-01-29
Thank you! It worked.

---

### Post by kurt18947 on 2013-01-30
For others with the same question, There may be another option in gnome shell.  Open overview - tap the Super key - and type 'sta'.  One of the choices should be startup apps.  It took me a little while to get used to the gnome-shell way of doing things.  Now however I find gnome 2/MATE inefficient.  If you're new to gnome-shell, I'd recommend a visit to extensions.gnome.org.  There are a few things there I find useful.

---

