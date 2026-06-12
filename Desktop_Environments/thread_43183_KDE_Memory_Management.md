---
title: "KDE Memory Management"
date: 2005-06-21
forum: Desktop Environments
---

### Post by AdrianVeidt on 2005-06-21
Guys, my Totem is broken in KDE and I can't get Muine to play songs in KDE either. Totem says "Can't open the resource for playing". I have all of the codecs, and Totem works in Gnome. Muine, from a terminal, says "segmentation fault" and closes wihtout further comment. Muine also works in Gnome.

---

### Post by Knome_fan on 2005-06-21
First off, I'd recommend Kaffeine as a movie player in KDE. As it also uses xine as a backend it will also use the same codecs totem does.

About your totem problem, I think (but I'm only guessing here) that it's complaining about your sound device being used by some other process, probably arts, the kde sound daemon. 
I'm not exactly sure, how to solve this, but you could try to open the Control Center, go to Sound & Multimedia, choose sound system and tell arts to shutdown after a second. This should make the sound device available to other applications not using arts.
It also might be a good idea to turn off all sound events as otherwise arts will be restarted everytime there is an event and you'll have the same problem again.

Sorry, no clue about your muine problem.

---

