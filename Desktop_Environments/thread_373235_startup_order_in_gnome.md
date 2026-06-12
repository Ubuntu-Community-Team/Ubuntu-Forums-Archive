---
title: "startup order in gnome"
date: 2007-03-01
forum: Desktop Environments
---

### Post by KhaaL on 2007-03-01
I wonder how I can change the startup order of my programs in gnome? I need gnome-terminal to start *after* beryl has initialized or the window attribs plugin won't take effect...

---

### Post by energiya on 2007-03-01
A nasty solution would be to make a script something like
```

#script to start gnome-terminal
sleep seconds
gnome-terminal

```
and start it before beryl. Change "seconds" to suit your needs (2,..5, ...)

---

### Post by orb9220 on 2007-03-01
goto systems>prefs>sessions

On current session you can change the order there by giving beryl a lower order like 39 and give terminal a higher order like 80 and make sure that on first tab session options you have automatically save changes to session checked.

---

### Post by KhaaL on 2007-03-01
making a startup bash script worked better than using gnomes internal session manager. for some reason, it didn't make gnome-terminal start late enough for the window attribs plugin to take effect...
thanks for the help!

---

### Post by Neo4 on 2007-03-09
i'm with the same problem!

with gnome session manager I can't start Eterm After devilspie!! :( 

using ubuntu edgy.

anyone can help?

---

