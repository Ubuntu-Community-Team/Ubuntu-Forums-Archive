---
title: "Dependency question"
date: 2007-04-10
forum: Desktop Environments
---

### Post by machoo02 on 2007-04-10
Does anyone else notice that sometimes package dependencies don't exactly make sense?  For example, I generally don't use a desktop email client, and therefore would like to remove Evolution.  I start removing components, but when I get to removing extra libraries such as llibebook, the list of additional packages to be removed contains some things that I wouldn't really consider as being dependent on the Evolution address book client library.  For instance:

[LIST]
[*]bug-buddy
[*]gnome-panel
[*]gnome-terminal
[*]nautilus
[*]nautilus-cd-burner
[*]gnome-control-panel
[/LIST]Why would gnome-terminal be dependent on an address book library?

---

### Post by gordebak on 2007-04-11
I think it is because of the ubuntu-desktop package. Maybe first you should remove that package. It is dummy.

---

### Post by machoo02 on 2007-04-11
I've already removed ubuntu-desktop, which is what allowed me to remove *parts* of Evolution (i.e., main program binaries).  It's only when trying to clean up all of the extra libraries, which I assume would only be needed by Evolution, that the dependency monster enters the room.

---

