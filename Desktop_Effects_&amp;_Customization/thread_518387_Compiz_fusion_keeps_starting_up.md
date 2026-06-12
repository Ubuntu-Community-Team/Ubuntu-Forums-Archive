---
title: "Compiz fusion keeps starting up"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by coront on 2007-08-05
Hey, I wanted to disable compiz fusion and stick with metacity again because I had some problems with video playback. The thing is that I remove compiz fusion from the startup programs in sessions and changed it for metacity in the configuration editor. However it keeps starting up. How do I completely remove compiz fusion?

---

### Post by the yawner on 2007-08-05
Hi. Please try out the following:

- Alt+F2 then run *gconf-editor*
- Check the tree desktop>gnome>applications>window manager
- See if the value for default is set to */use/bin/metacity*

If you know that the above setup is correct, or have confirmed that this is set then do the following:

- Check the Current Session tab under sessions
- See if compiz --replace is listed there along with other related commands (possibly emerald --replace and avant-window-navigator if you also used these. )
- Highlight it, click remove then apply
- Restart your system and check

---

