---
title: "Is it proper to delete folders in gconf?"
date: 2007-11-05
forum: Desktop Environments
---

### Post by david.rahrer on 2007-11-05
Say you install an app, don't like it, and uninstall it.  Usually it leaves the dot folders in ~/ which I understand - I delete them if I don't want to use it again.  But sometimes there are bits left in gconf as well, folders obviously belonging to the uninstalled program (named after it).  If I know these are not in use, is it proper to just delete them?  Or is there a procedure to follow?  Up to now, I've just deleted them when I noticed, but I'm curious if this is best or safe.  Hope that makes sense :)

---

### Post by Happy_Man on 2007-11-05
Well, if it's not safe, the next time you start that app up, it'll just recreate the folder. the settings folders in Linux are not anything like the Windows Registry, nor is Gconf anything like Regedit. Gconf is basically another way to access settings. It can no more change internal workings than could, say, Firefox.

---

### Post by david.rahrer on 2007-11-05
Thanks.  I had a feeling but I've never found good documentation to explain just what gconf stores as opposed to the dot files.  I really love the way most configurations are stored in a logical set of folders in home.  I guess I should read up on all that now.  

PS: Love your Avatar!

---

