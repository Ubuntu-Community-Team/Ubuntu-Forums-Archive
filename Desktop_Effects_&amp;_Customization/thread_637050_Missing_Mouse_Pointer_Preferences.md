---
title: "Missing Mouse Pointer Preferences"
date: 2007-12-10
forum: Desktop Effects &amp; Customization
---

### Post by BakerBug on 2007-12-10
I am running Gutsy and can no longer find the mouse pointer preferences.  I am trying to enable the mouse highlighter when pressing the Ctrl key.

Thanks!

---

### Post by acowboydave on 2007-12-11
Right click a free spot on your your desktop, in the window that appears click change desktop background..then click theme..click customize..click pointer..adjust from there.;)

---

### Post by BakerBug on 2007-12-11
I'm still not seeing what I need.

I want to enable the option so that when I press <ctrl> the mouse cursor will visually change as to indicate it's location on the screen.  I have 4 PCs all using the same keyboard and mouse linked with Synergy.  So I have one mouse pointer that could be anywhere on 1 of 4 screens.  I'm not trying to change the normal look of the mouse pointer, I need to be able to locate my mouse pointer when it gets "lost".

Thanks!

---

### Post by BakerBug on 2007-12-12
:guitar:

---

### Post by pauledwards03 on 2007-12-17
I have the feature enabled, but wish to disable it and I cannot find it! It interferes with gaming, as there is no way to ctrl-click inside my game (city of villains) with this feature enabled

Is there a key in the gconf-editor that can do this???

/schemas/desktop/gnome/peripherals/mouse/locate_pointer cannot be changed! (Currently pairs and schemas can't be edited. This will be changed in a later version.)

---

### Post by pauledwards03 on 2007-12-17
update: by changing the %gconf.xml file in :~/.gconf/desktop/gnome/peripherals/mouse

<entry name="locate_pointer" mtime="1188781524" type="bool" value="true"> to
<entry name="locate_pointer" mtime="1188781524" type="bool" value="false">

it solved the problem :-D

---

### Post by FuturePilot on 2007-12-17
An easier way would be to open gconf-editor and navigate to desktop>gnome>peripherals>mouse and check the locate_pointer box

---

### Post by BakerBug on 2008-02-20
> **FuturePilot said:**
> An easier way would be to open gconf-editor and navigate to desktop>gnome>peripherals>mouse and check the locate_pointer box

This worked!

So why is this option now in such an obscure place when it used to be easily found under System>Preferences>Mouse?

---

### Post by DaymItzJack on 2008-02-20
You could of also used the compiz fusion water plugin for this.

---

