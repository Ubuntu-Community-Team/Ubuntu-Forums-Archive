---
title: "Lost adressbook in .evolution"
date: 2005-04-17
forum: Desktop Environments
---

### Post by ploum on 2005-04-17
I've installed Ubuntu Hoary instead of Debian Sarge. Before launching Evo for the first time, I've put my backup in ~/.evolution, so Evolution would normally launch as the old 2.0.6 from Sarge.

 All was fine...

except that I've no more others adressbooks than "Personnal" :-(  And now, I need them.

How can I take them back ?  I don't really understand the .evolution structure.

Thx for help

---

### Post by ploum on 2005-04-17
I find the solution :

restore the file ~/.gconf/apps/evolution/addressbook/%gconf.xml

It's really a bad idea, IMHO, to store this information elsewhere. 
[http://bugzilla.gnome.org/show_bug.cgi?id=300940](http://bugzilla.gnome.org/show_bug.cgi?id=300940)

---

### Post by hamil on 2005-04-17
To late for me...
Anybody know howto restore my adressbook, with only the /home/.evolution/ folder available?

Would be very happy foor any kind of advice.... :)

Brgds
/Lasse

---

