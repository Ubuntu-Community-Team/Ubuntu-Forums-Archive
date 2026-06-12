---
title: "GnomeBaker quit working"
date: 2006-08-13
forum: Desktop Environments
---

### Post by as400 on 2006-08-13
I've always used this app for my CD DVD burning needs.
Since I dont know when... it quit working. I launch the app via the menu, it clocks and quits before the GUI ever comes up.
Looking for advice here. Thanks!

OS: Ubuntu 6 on PC


____________
AS/400

---

### Post by JerMe on 2006-08-13
try running **gnomebaker** through the terminal (Applications > Accessories > Terminal) and see what the output is.

---

### Post by as400 on 2006-08-13
Here we go:

[COLOR="Red"]ecarvalho@ubuntu:~$ gnomebaker
GTK Accessibility Module initialized

GThread-ERROR **: GThread system may only be initialized once.
aborting...
Aborted
ecarvalho@ubuntu:~$[/COLOR]

What do you make of it?

---

### Post by JerMe on 2006-08-13
From [http://www.ubuntuforums.org/showpost.php?p=1283681&postcount=2:](http://www.ubuntuforums.org/showpost.php?p=1283681&postcount=2:)

> The problem is gnomebaker is not getting along with the accessibility
module. If accessibility support is not a requirement for you, it can be
disabled with the gconf-editor. The relevant key
is /desktop/gnome/interface/accessibility. Uncheck the box and then
restart your session.

---

### Post by as400 on 2006-08-13
This may be a dumb question but how to I get to gconfig-editor?

Thank you in advance

AS/400

---

### Post by vijirajan on 2006-08-13
Using Applications->System->Configuration Editor menu item.

---

### Post by as400 on 2006-08-13
Got it! Thank you.

AS/400

---

### Post by JerMe on 2006-08-13
or type **gconf-editor** at the terminal.

---

