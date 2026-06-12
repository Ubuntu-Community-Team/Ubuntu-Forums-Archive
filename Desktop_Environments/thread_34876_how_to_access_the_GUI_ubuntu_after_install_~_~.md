---
title: "how to access the GUI ubuntu after install ~_~"
date: 2005-05-16
forum: Desktop Environments
---

### Post by Meilad on 2005-05-16
Hey there, Ran the live cd of ubuntu 5.04 and it was pretty good so I installed it.

Except now by default it loads up Gnome or whatever the command line interface is called. I'm just wondering how I can access the Graphical Interface for Ubuntu

Cheers!

---

### Post by NeoChaosX on 2005-05-16
Type in "startx" at the command line and you should get into GNOME (which is the name of the GUI, not the command line).

But it does sound like something's broken if it's booting into the command line. If there's an error when doing startx, tell us what it is.

---

### Post by dave9191 on 2005-05-16
Gnome is the graphical interface and it loads up by default after the install. If you are getting the command line, then something must have gone wrong with the install. 

login in and type 

sudo apt-get -f install

That will try to fix any problems. 

Dave

---

### Post by Meilad on 2005-05-16
[QUOTE=dave9191]Gnome is the graphical interface and it loads up by default after the install. If you are getting the command line, then something must have gone wrong with the install. 

login in and type 

sudo apt-get -f install

That will try to fix any problems. 

Dave[/QUOTE]
 uh i think this is because I typed server at the beginning of the install prompt rather than enter for default config.

Yes?

Cheers!

---

### Post by dave9191 on 2005-05-16
That would definatly explain it :) 

You only have a minimal install, which doesnt have any graphical tools. It is possible to install everything yourself from there, but I would just suggest that you install again with a full intsall instead. 

Dave

---

### Post by Meilad on 2005-05-16
[QUOTE=dave9191]That would definatly explain it :) 

You only have a minimal install, which doesnt have any graphical tools. It is possible to install everything yourself from there, but I would just suggest that you install again with a full intsall instead. 

Dave[/QUOTE]
 yea it's just doing stage 2 now. Unpacking loadsss of stuff.

---

### Post by dave9191 on 2005-05-16
It should be done in 30 min or so :) And then you can log in with the user account you created during install into a nice pretty ubuntu gnome desktop :)

---

