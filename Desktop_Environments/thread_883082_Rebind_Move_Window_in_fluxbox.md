---
title: "Rebind Move Window in fluxbox"
date: 2008-08-07
forum: Desktop Environments
---

### Post by ap0110 on 2008-08-07
My system is a Xubuntu base with xfce removed after I made the switch to fluxbox.  
I cannot find a way to change the shortcut for move window in fluxbox.  I have [searched]("http://http://ubuntuforums.org/showthread.php?t=455370") around in the forums.  
However I can't find where to change this setting.  I've looked at the list of shortcuts on the [fluxbox wiki]("http://fluxbox-wiki.org/index.php/Keyboard_shortcuts") however nothing looks like its the right thing.  Any ideas?

---

### Post by ap0110 on 2008-08-07
I did some more research and I found the answer.

session.modKey: Mod4
-allows to use the winkey to resize and move windows and have Mod1 (Alt) free for using blender or Maya.

you add this setting to ~/.fluxbox/init

---

