---
title: "[SOLVED] Window Manager is messed up..."
date: 2008-08-30
forum: Desktop Environments
---

### Post by the8thstar on 2008-08-30
Hello all,

I have a bugging problem here. Every time I start Ubuntu, the title bar are absent and none of the shortcuts I use in Compiz work (like Show Widget, Expo, etc...) I have to reload the window manager with the Compiz Fusion icon menu.

What could I do to solve this problem?

---

### Post by pytheas22 on 2008-08-30
If reloading compiz solves the problem, then it would probably work to run that command automatically each time you log into Gnome.  Go to System>Preferences>Sessions.  Under the "Startup Programs" tab, click Add, then put this command in the "command" field:
```

compiz --replace
```

Give the command any name you like, and make sure the box is checked to run it each time you log in.  Then log back out and back in and see if the issue gets resolved automatically.  Please let us know.

---

### Post by the8thstar on 2008-08-30
I followed your suggestion and it worked! Thanks!

---

