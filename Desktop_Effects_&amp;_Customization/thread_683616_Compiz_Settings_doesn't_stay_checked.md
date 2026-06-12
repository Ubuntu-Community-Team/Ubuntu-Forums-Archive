---
title: "Compiz Settings doesn't stay checked"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by rogeriovinhal on 2008-01-31
Hello, this is the third time I am trying to make a post to solve this problem, and I've searched other posts as well, but no solution to this yet.

I have a very picky problem. I have Compiz Fusion working with Advanced Desktop Effects Settings installed, have made my own settings in it, but sometimes after I restart some plugins like "move", "put", "desktop decorations" just revert to disabled. Every other configuration I made just stays as I did them, but these ones seems to disable themselves in a non-deterministic way, sometimes one of them, sometimes two, sometimes them all, sometimes none of them.

Please help me because I have this bug since I installed Ubuntu 7.10 (that's quite a long time) and have seen no solutions to this. It is a very important problem, since it keeps me from moving, resizing and even seeing the window decoration sometimes.

---

### Post by organica on 2008-02-10
This might be a little off the wall, but since no one is helping you I'll start.

- Try deleteing the compiz folder in the hidden folder ".config" in you home directory. Then hit ctrl-alt-backspace.  After login, does this fix it?

- Check the time stamp for the ~/.config/compiz/compizconfig/config file.  Has it been changed recently?  Are you changing it or is something else changing it?

- Try setting the Compiz Manager to exactly the way you want it then save your settings in the preferences area.  Then load your custom compiz settings from the file you just saved.

---

### Post by rogeriovinhal on 2008-03-17
I've tried everything you said and something more...

- Changed Compiz in Preferences to use a flat file.
- Located that file (.config/compiz/compizconfig/Default.ini)
- Removed all write permission on that file

And guess what? The plugins stopped to get unchecked, BUT they didn't stop to stop working.

Recently this is always happening like this:

- Everytime I restart, the resize plugin becomes unchecked 100% of the time.
- If the resize plugin is not checked, the preview AND move plugins MAY become unchecked.
- If all of the above plugins are not checked, Window Decoration has an even lower probability to become unchecked.

I don't have any idea of what this might be. It just challenges everything I have seen before in any type of configuration.

---

### Post by mrmiserable on 2008-03-17
open ccsm
under preferences on left make sure plugin list is set to automatic 
hope this helps

---

### Post by rogeriovinhal on 2008-03-17
> **mrmiserable said:**
> open ccsm
under preferences on left make sure plugin list is set to automatic 
hope this helps

It was already set to automatic... :(

---

### Post by mrmiserable on 2008-03-17
ok have you tried to set them in gconf-editor apps-compiz-general active plugins
or export file in ccsm preferences and use that 
these are all suggestion as im not really sure now
weird

---

### Post by mspaul on 2008-05-31
I'm having the same problem

---

