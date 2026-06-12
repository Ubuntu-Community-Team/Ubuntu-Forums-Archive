---
title: "Editing &quot;Create New&quot; Files Menu"
date: 2005-05-09
forum: Desktop Environments
---

### Post by schillelagh on 2005-05-09
I have made a fairly recent migration over to the KDE desktop and generally speaking I do enjoy it.

However, one thing that drives me up the wall is the "Create New..." menu when you right-click in Konqueror. There is nothing particularly useful there besides folders and there does not seem to be an easy way to add files for things such as Openoffice.org documents or bash/perl scripts.

I've scoured Google and several forums to no avail. Is there a way to hack that menu dialog such that I can create other files besides Koffice files? Ideally I would like something analogous to Gnome's template functionality, where I have previously stored all my templates for various documents.

Thanks!

---

### Post by BryanFRitt on 2008-07-14
Try:
[http://www.techknack.net/2008/03/add-entries-to-konquerors-create-new.html](http://www.techknack.net/2008/03/add-entries-to-konquerors-create-new.html)

(optional) and then:

[http://www.kde-apps.org/content/show.php/Create+New+Template+Service+Menu?content=53353](http://www.kde-apps.org/content/show.php/Create+New+Template+Service+Menu?content=53353)
be sure to read all the comments, because directions can be confusing.
copy or move the service-installer.sh to ~/bin/

[http://www.kde-look.org/content/show.php?content=11435&forumpage=0](http://www.kde-look.org/content/show.php?content=11435&forumpage=0)
right click on add_action.desktop and Actions->Install Service->(pick one, like the first one which will put a copy of itself to ~/.kde/share/apps/konqueror/servicemenus (or you could put it there manually to install it))
-
Not really sure how to use stuff I put down as optional(from above)(as of typing this.)

---

### Post by schillelagh on 2008-07-18
Awesome, thanks! I have never found such a succinct explanation.

---

