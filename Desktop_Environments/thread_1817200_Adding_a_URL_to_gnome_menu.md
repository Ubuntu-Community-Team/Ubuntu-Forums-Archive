---
title: "Adding a URL to gnome menu"
date: 2011-08-03
forum: Desktop Environments
---

### Post by r.darwish on 2011-08-03
I want to add an entry in gnome menu that points to Python 2.6 documentation's main page, which can be found in:
/usr/share/doc/python2.6-doc/html/index.html

I'm trying to do that using the GUI, so I clicked "New Item", chose "Location" as type, and browsed to the html file, resulting a URL that starts with file:///.
When I click OK the dialog box is closed without any errors, but I cannot see my new entry in the menu.

I realize that I can specifically launch Firefox with the URL as its argument, but if I ever want to switch the default browser the documentation will be still open by Firefox. This will probably be the same if I ever want to add non-executable files to the gnome menu. Isn't there way to do that?

---

### Post by koleoptero on 2011-08-03
try xdg-open "path/to/file"

---

### Post by r.darwish on 2011-08-04
It worked. Thank you! :-)

---

