---
title: "cant access user profiles in console anymore"
date: 2009-04-12
forum: General Help
---

### Post by ayastona on 2009-04-12
my console/terminal screen changed colors and stuff.. when i go to terminal>change profile.... "change profile" is grayed out.. 

how do i change it back to my regular profile? i am logged in as the correct "admin" user...

---

### Post by drs305 on 2009-04-12
I you opened it as root you might have done so with root's profile instead of your profile. Try closing the terminal and opening a new one normally. 

If you are running gnome-terminal, the user's profiles are stored in .xml files ~/.gconf/apps/gnome-terminal/profiles. Rather than editing the profiles, it might be simpler just to delete them and let terminal recreate a default one the next time it starts up.

You could also try renaming them, restarting the terminal to see if it runs properly, then copying your profiles into the new default folder.

---

