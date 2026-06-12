---
title: "How to clean-kill a KDE app ?"
date: 2009-02-09
forum: Desktop Environments
---

### Post by dargaud on 2009-02-09
Hello all,
I've left kmail, firefox and other stuff runnning on my home PC and I would like to use those app remotely through an X session. So I first need to kill them. I know I can do a "killall kmail", but is there a way to force a clean exit ? Some flag of kill ?
Thanks.

---

### Post by jacksaff on 2009-02-09
Kill sends a term signal so the app should exit properly.
kill -9 sends a sigkill which is nastier.
You can kill apps while running top by hitting k. It asks you exactly what you want to do which might be a bit more what you're looking for.

---

### Post by ajgreeny on 2009-02-09
In gnome the xkill command in the Alt+F2 run dialog will make your cursor into a cross. Place that cross on a window and left click and the window will close.  I'm sure I remember something similar in kde, but can't remember exactly, though I think it is Ctrl+Alt+Esc to turn the cursor into a Skull & Crossbones.  Give that a try.

---

