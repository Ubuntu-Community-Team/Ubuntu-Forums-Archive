---
title: "Gnome - Disable a Gnome Panel"
date: 2008-04-04
forum: Desktop Environments
---

### Post by Naatan on 2008-04-04
Hi, I have a laptop from work that I take home with me, at work I have a monitor connected to the laptop but at home I just use the laptop..

Now I've sprung the idea to create a custom x session for work, so that I can execute certain commands when logging in on my work..

I'd have to remove the gnome panel on the second monitor when I login on the "real" gnome session and add it on the "work" session.. preferrably I'd like to simply disable and enable it so that it's not actually deleted..

can anyone tell me if this is possible and if so.. how ?

---

### Post by Gen2ly on 2008-04-04
hmm this is a bit tricky.  Gnome starts as a group of applications one of these being gnome-session which is tied to gnome-panel.  To do this, I would think that a new gnome exec would have to be created, and that would be an awful alot of work.  Probably a better way to do this is to create a script to start and stop the programs you need.  If you haven't done bash scripting before here's a good start to it:

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)

Also I can tell you that to quit gnome-panel it will have to be released by gnome-session.  You can do this by typing this:

```
gnome-session-remove gnome-panel
```

Hope this helps to start.

---

