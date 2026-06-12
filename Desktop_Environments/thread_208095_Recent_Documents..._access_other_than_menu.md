---
title: "Recent Documents... access other than menu?"
date: 2006-07-03
forum: Desktop Environments
---

### Post by naked on 2006-07-03
Is there a way to access recent documents other than through the menu?

I'd like to have a keyboard shortcut to them if possible.  Is this a special nautilus folder or something?

L

---

### Post by aanderse on 2006-07-03
Under your home folder there is a file called .recently-used which follows an xml format which contains the list of the most recently used items you are looking for.

---

### Post by aanderse on 2006-07-03
please delete this message, i posted in the wrong message ...

---

### Post by cwmccabe on 2006-07-09
(bump)

I'd like to second this question.  Is there an -easy- way to set a Recent Documents menu somewhere other than in Menu >> Places >> Recent Documents.  I would like to have access to the menu from the main taskbar.  Is this possible, or is anything like this possible?  Just as *naked* would like to be able to have access to the list through a keyboard shortcut, I'm wondering if it could be accessed by a click to an icon on the taskbar.

---

### Post by amanda on 2007-05-09
There is an XML file in my home directory called ".recently-used" but  "recent documents" aren't part of the Ala Carte menu editor and I haven't been able to find any other way to make the list accessible on a panel.


This: [http://www.advogato.org/person/snorp/diary.html?start=9](http://www.advogato.org/person/snorp/diary.html?start=9) looked promising, but it seems to be ancient.
This: [http://developer.gnome.org/doc/API/2.0/gtk/GtkRecentChooserMenu.html](http://developer.gnome.org/doc/API/2.0/gtk/GtkRecentChooserMenu.html) looks interesting, too.

---

### Post by amanda on 2007-05-09
I'm pretty sure that this [Recent Documents Widget Thingie]("http://developer.gnome.org/doc/API/2.0/gtk/RecentDocuments.html")  is the right direction, but I have no idea what to do with a [GTK+ Widget besides look it up]("http://en.wikipedia.org/wiki/GTK").

I am willing to bet that [this guy knows]("http://log.emmanuelebassi.net/archives/2007/02/come-and-see/") but I'm not sure how to ask without sounding dumb. What is the question? "Umm, you. help. widget." ? No.

---

