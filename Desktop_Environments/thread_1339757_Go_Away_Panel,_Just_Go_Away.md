---
title: "Go Away Panel, Just Go Away"
date: 2009-11-27
forum: Desktop Environments
---

### Post by Mahngiel on 2009-11-27
So i've found myself a nice little dock that i've gotten all nice and rigged up.  But I have to stare at this ugly gnome panel with nothing on it.  So, oh wise wisdom amongst the Ubuntu populace, please tell me how to get rid of this last standing, hard to die, panel.

thx ;)

>>Karmic<<

---

### Post by rednano12 on 2009-11-27
RightClick -> Delete this Panel

---

### Post by Mahngiel on 2009-11-27
> **Mahngiel said:**
> ... how to get rid of this last standing, hard to die, panel.


i'm fully aware of how to get down to one panel. but gnome likes you to keep one. try it, i bet you can't right click > delete the s.o.b.

---

### Post by Hamchan on 2009-11-27
Try "killall gnome-panel" in the terminal.

---

### Post by nerdy_kid on 2009-11-27
there is an entry in GNOME's configuration editor that defines the session's required programs , sorry cant be more clear -- im running KDE and forgot the config editor's name.  Anyway, gnome-panel is in there, so if you delete it and then run killall gnome-panel at login...(you might not have to..)

hope this helps a little

---

### Post by Hamchan on 2009-11-27
> **nerdy_kid said:**
> there is an entry in GNOME's configuration editor that defines the session's required programs , sorry cant be more clear -- im running KDE and forgot the config editor's name.  Anyway, gnome-panel is in there, so if you delete it and then run killall gnome-panel at login...(you might not have to..)

hope this helps a little

Do you mean gconf-editor?

---

### Post by Mahngiel on 2009-11-27
Hamchan:  Is there a sustainable way to do this? so after every reboot i don't have to re-kill?

nerdy_kid: do you remember which part of the tree it would be under? perhaps the settings daemon?? i'm sure i could find something related to panels = 1

---

### Post by ajy0852 on 2009-11-27
Open a terminal, and type
```
gconf-editor
```
and hit enter.
Use the left pane to navigate to Desktop -> Session -> Required Components. Delete "gnome-panel" from the configuration. There does not need to be anything set in "panel" (the key can remain empty).

---

### Post by josephellengar on 2009-11-27
I saw another thread about this problem the other day.  Can't find it now, but it has a really easy solution.  Just do an 
```

apt-get remove gnome-panel

```
 Gets rid of the package and then the panel won't load.  You can't do a killall or pkill gnome-panel because that will automatically reboot.  Just try it.  Hope I helped!

---

### Post by Mahngiel on 2009-11-27
ajy0852, couldn't find it at first. posted a laughable pic to display to you that i don't have ' session' under "desktop". then i got cute and went _Desktop -> Gnome -> Session -> Req. Comps_ and found it. thanks to all of ya.

---

### Post by tacantara on 2009-11-27
Apparently, the ability to permanently remove the top panel isn't a feature available in 9.10.  I've tried to remove it by right-clicking the panel (option is grayed out) and through gconf-editor (can't be deleted, and the edit options are grayed out....even when you gksudo the gconf-editor).

---

### Post by ajy0852 on 2009-11-27
> **Mahngiel said:**
> 

oh ya? ain't got it. and yes... gnome-sessions IS installed

Oops, sorry! I should have said desktop ->**gnome** -> session -> required_components.

So, it should be under Gnome. My bad.

Edit: Looks like you found it. I should have waited a second before posting. My bad again. ;)

---

### Post by tacantara on 2009-11-27
And this panel thing gets worse....on a hunch, I checked under schemas > desktop > gnome > session > required components. The panel is listed as a schema, but when you double-click to edit, the following error message appears: 

```
Currently pairs and schemas can't be edited. This will be changed in a later version.
```

---

### Post by nerdy_kid on 2009-11-28
of course there always is
```

sudo chmod -x /usr/bin/gnome-panel

```

that WILL get rid of it

---

