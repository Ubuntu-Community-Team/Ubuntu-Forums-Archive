---
title: "Help, no Help!"
date: 2005-12-18
forum: General Help
---

### Post by John Jason Jordan on 2005-12-18
When I click on System > Help I always get a window popping up that says "The application "yelp" has quit unexpectedly." There are buttons for Restart, Close and Inform Developers. "Restart" just produces another such window. It has always been this way. I have never been able to see the Ubuntu Help files.

Does anyone have any idea what is wrong?

---

### Post by ranf on 2005-12-18
Open a terminal and run yelp from it. One usually gets at least some error messages.

---

### Post by John Jason Jordan on 2005-12-18
[QUOTE=ranf]Open a terminal and run yelp from it. One usually gets at least some error messages.[/QUOTE]
Why didn't I think of that?

OK, here is a copy and paste of the error messages:

jjj@Devil5:~$ yelp
I/O warning : failed to load external entity "/home/jjj/.gnome2/yelp-bookmarks.x bel"

(yelp:13643): Gtk-CRITICAL **: gtk_stock_lookup: assertion `stock_id != NULL' fa iled
plugin_get_value 1
plugin_get_value 2
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot o pen shared object file: No such file or directory]

Looks like some stuff is missing. I just now opened Synaptic and reinstalled it. Still won't open when I click on System > Help. Tried again from the command line and got exactly the same errors as above.

More suggestions?

---

### Post by Madpilot on 2005-12-18
File a bug and get the developers involved?

[http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)

---

### Post by Kevinator on 2005-12-18
You can find both of those libraries in the software repositories. Just use Synaptic to install them. No idea why you don't have them installed already, though.

---

### Post by John Jason Jordan on 2005-12-18
[QUOTE=Madpilot]File a bug and get the developers involved?
[http://bugzilla.ubuntu.com/](http://bugzilla.ubuntu.com/)[/QUOTE]
Already did that from the error message popup window.

---

### Post by John Jason Jordan on 2005-12-18
[QUOTE=Kevinator]You can find both of those libraries in the software repositories. Just use Synaptic to install them. No idea why you don't have them installed already, though.[/QUOTE]
Not in my Synaptic. I have:

libxext6 (installed)
libext-dev
libxt6 (installed)
libxt6-dbg
libxt-dev
libxt-java (installed)

---

