---
title: "Window borders on Unity"
date: 2012-04-04
forum: Desktop Environments
---

### Post by msajjadi on 2012-04-04
I lost my window borders (and title bar and so the close button).

I don't know how that happened.

How can I get it back?

---

### Post by msajjadi on 2012-04-04
Anybody there?

I read somewhere, I should use something like:
```
metacity --replace
```

But I don't think it's for unity, maybe it's for Gnome classic.

Help please...

---

### Post by zombifier25 on 2012-04-05
If you're using Unity 3D, looks like you messed up Compiz somehow. Try reseting the profile:
```
gconftool --recursive-unset /apps/compiz-1
```
Or this if 11.04:
```
gconftool --recursive-unset /apps/compiz
```

---

### Post by Gremlinzzz on 2012-04-05
CompizConfig Settings Manager
Once open, scroll down to the Effects section, where you will see Window Decoration is not enabled. Simply click the check box to the left of it, and you should see your window borders reappear.

---

### Post by Gremlinzzz on 2012-04-05
if it isn’t installed, just run sudo apt-get install compizconfig-settings-manager in a terminal.:popcorn:

---

### Post by stinkeye on 2012-04-05
Usually running in the terminal...
```
gtk-window-decorator --replace & disown
```
will bring them back.

---

