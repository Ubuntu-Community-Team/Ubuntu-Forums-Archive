---
title: "Removing keyboard shortcuts in Exaile"
date: 2009-04-25
forum: Desktop Environments
---

### Post by booljayj on 2009-04-25
I have an interesting problem. I am using crunchbang, which is based on ubuntu, and I have exaile as my media player. I recently updated to jaunty --by replacing the word 'intrepid' with 'jaunty' in my sources.list-- and exaile now seems to respond to global keyboard shortcuts. I would like to know how to disable all keyboard shortcuts in exaile.

You see, I am using openbox to handle my keyboard commands for exaile. This allows me to use the stop button to hide/show exaile (by mapping it to the command 'exaile'). Since the upgrade, whenever I press the stop button, it actually stops the music and furthermore does not hide/show the window. Openbox is still set correctly, but now something is interfering with the way I'd like it to work. I went into gconf-editor and changed the stop entry under gnome_settings_daemon to nothing, enabled both shortcut plugins in exaile and set every command to nothing, and it did not help.

Bottom line: the error seems to be within exaile itself, because nothing else on my system seems to be handling any keyboard commands. How exactly does exaile map it's keyboard commands internally, and can they be disabled?

---

### Post by booljayj on 2009-04-26
Nevermind. Turns out setting all the shortcut plugins to nothing solved the problem, but it took a little while for exaile to catch on.

---

