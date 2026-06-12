---
title: "Switching From Command Line to GUI"
date: 2009-03-17
forum: General Help
---

### Post by SoulMazer on 2009-03-17
To prevent confusion, I am not running a server edition. I am running Ubuntu 8.10.

So, sometimes I like to boot only to the command line (Control + Alt + F2), since I just need to do a quick thing. However, I occasionally press those keys without meaning to. What is the easiest way to switch to my GUI desktop (Gnome) so that I don't have to restart my entire computer?

Much thanks in advance.

---

### Post by batharoy on 2009-03-17
Have you tried
```
startx
```

---

### Post by Vaphell on 2009-03-17
CTRL+ALT+F7 switches back to gnome session on my 8.04

---

### Post by SoulMazer on 2009-03-17
EDIT:

Sorry, I didn't see that there were two posts. I get an error when attempting to "startx", so I guess Control + Alt + F7 is fine.

Thank you very much guys/girls!

---

### Post by ruel- on 2009-03-17
you could
```
 sudo apt-get install ubuntu-desktop
```

then at the login, type startx, and it will get you to the login GUI.. choose gnome.. you're done!

---

