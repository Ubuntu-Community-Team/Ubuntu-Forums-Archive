---
title: "Change gnome_terminal window's geometry with command?"
date: 2009-06-14
forum: General Help
---

### Post by Generic_Guy on 2009-06-14
I already know about "gnome-terminal --geometry 80x25", but I want a way to change a script's own terminal geometry with a command. Any chance of my knowing how? :)
(in case you're wondering, I'm making a DoomRL app launcher)

---

### Post by kerry_s on 2009-06-14
not sure what you mean, are you talking:
gnome-terminal --geometry 80x25 **-e script**

---

### Post by Generic_Guy on 2009-06-14
Well, that works, but that doesn't answer my question. That's creating a new terminal with a certain geometry and a default script. I want a command to change the geometry of a terminal in-place. Then I wouldn't need all these arguably unnecessary arguments. :|

---

### Post by kerry_s on 2009-06-14
so you want to modify a running process?
why cant you just grab a corner and make it bigger?

---

