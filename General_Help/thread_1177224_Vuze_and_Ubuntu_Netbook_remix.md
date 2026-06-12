---
title: "Vuze and Ubuntu Netbook remix"
date: 2009-06-03
forum: General Help
---

### Post by NewNerd99 on 2009-06-03
Have installed Vuze on a Kogan netbook (1.6G Atom) and when I click the icon nothing happens.

Any advice on what to check next would be appreciated

Chris

---

### Post by jjbasken on 2009-06-03
Try opening a terminal and running "vuze", if there are any error messages when running they will display in the terminal.

---

### Post by NewNerd99 on 2009-06-04
Thanks for that. This is what Terminal said. 

Seems it may not have installed properly, or it's missing a component?







chris@chris-netbook:~$ vuze
exec: 11: /usr/lib/jvm/java-6-openjdk/jre/bin/java: not found
chris@chris-netbook:~$

---

### Post by flamacue on 2009-07-11
Looks like either you don't have java installed, or it's not in your path.

I don't know if you installed Vuze from the Ubuntu repositories or downloaded the installer from their site, so I'm not sure what to tell you next.  I recommend downloading the installer, b/c the Ubuntu repository (even Jaunty's) is way back on version 3.

See the Initial Setup Guide, and also follow the linked Java Guide in that document:

[COLOR="Blue"]_[http://azureuswiki.com/index.php/Initial_Setup_Guide](http://azureuswiki.com/index.php/Initial_Setup_Guide)_[/COLOR]

---

