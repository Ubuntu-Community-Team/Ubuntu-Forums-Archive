---
title: "Add Launcher to top panel via script?"
date: 2011-09-14
forum: Desktop Environments
---

### Post by cwhittier on 2011-09-14
I am running Ubuntu 9.04, and I am trying to add a launcher to my top panel via a script.

A few google hits said to use the gnome-panel-add command, located in /usr/lib/gnome-panel/  but I do not have that file on my system, it looks like it was removed at some point. Can anyone tell me how to do this?

P.S. I know how to do this via the GUI already, I don't need instructions on how to do that.

---

### Post by cwhittier on 2011-09-16
I've found a solution. If you have desktop files or 'launchers' created already, you can use  the script provided in the following link, to add them. Be weary  however, if for some reason the panel you are adding to currently has no  other objects on it, this script will not work right, because it wants  to append a comma to the existing list, assuming there are items already  in it. You'll have to modify it not to do that.

[http://blogs.warwick.ac.uk/mikewilli...ation_launcher]("http://blogs.warwick.ac.uk/mikewillis/entry/add_application_launcher")

---

