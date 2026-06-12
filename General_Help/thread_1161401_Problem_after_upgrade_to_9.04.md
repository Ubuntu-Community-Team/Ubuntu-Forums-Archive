---
title: "Problem after upgrade to 9.04"
date: 2009-05-16
forum: General Help
---

### Post by splicer on 2009-05-16
I just upgraded my work laptop to 9.04.  First thing I noticed is that all the window decorations are gone (i.e.: title bar, maximize, minimize, and kill buttons, window frame, etc) ... it's as if the window manager is not running?

I'm at a loss here ... anyone have suggestions?
[splicer]

---

### Post by soro2005 on 2009-05-16
Are you using desktop effects? What window manager? What window decorator? Type
```
metacity --replace &
```
into a terminal. If you use desktop effects, install and run fusion-icon and try out some of the options.

---

### Post by 5nak3 on 2009-05-16
If your problem is a compiz related problem i.e. compiz not loading the window decorations you might have to add compiz to the startup programs. To do so:

System -> Preferences -> Startup Applications -> Add

In the name field type compiz, and in the command field again compiz, finalize by pressing add.

Log out, log in and it should be ok!

---

### Post by splicer on 2009-05-16
Thanks, both of your suggestions were right on the mark!  By adding compiz to startup at login time, it's all fixed again!!

---

### Post by 5nak3 on 2009-05-17
Glad things worked out for you :D

If you could mark this topic as solved that would also be great as it allows people to know if the answer they are looking for is within the thread.

---

