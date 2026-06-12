---
title: "show clickable list of users at login screen?"
date: 2006-01-09
forum: General Help
---

### Post by metuwi on 2006-01-09
how can i show a list of users at the login screen? i know this is possible with kdm, but i dont know how. the show-list option in the login manager does not work--i even tried disabling then enabling it.

---

### Post by pelle.k on 2006-01-15
Do remember - issues like this have been answered in the past.
Use the search function people...
[http://www.ubuntuforums.org/showthread.php?t=23110&highlight=kdm+list+users](http://www.ubuntuforums.org/showthread.php?t=23110&highlight=kdm+list+users)

Anyway, to sum it up :)

> 

 kdesu kate /etc/kde3/kdm/kdmrc

 find the line with:
 
 UseTheme = true
 
 and change to:
 
 UseTheme = false
 
 You can then use Control Centre to turn the user list on.

---

