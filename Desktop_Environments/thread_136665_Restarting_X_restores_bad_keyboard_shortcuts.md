---
title: "Restarting X restores bad keyboard shortcuts"
date: 2006-02-26
forum: Desktop Environments
---

### Post by joehill on 2006-02-26
When I tried to reassign keyboard shortcuts to control rhythmbox from the "keyboard shortcuts" dialogue, for some reason it construed my "CTRL+SHIFT+a" as "a" and completely remapped my "a" key.  Same with "s".  Changing the shortcut back didn't help because it actually remapped the keyboard so the "a" was recognized as something else (something like 0x4f).

I thought I had solved the problem after reading a helpful thread where someone suggested resetting keyboard defaults in the System-> Preferences-> Keyboard-> Layouts dialogue.  It worked, but now every time I restart X, the "a" and "s" keys stop working and I have to reset my defaults.  This is very annoying because I use a number of layouts and have to reconfigure everything every time I start X.

There must be come configuration file where this remapping has been stored, but I've looked around and can't find anything.

---

### Post by Ramses de Norre on 2006-02-26
Helps changing it and then logging out whith save current setup?

---

### Post by joehill on 2006-02-26
Thanks for the suggestion.  Unfortunately it still doesn't work.

---

### Post by joehill on 2006-02-27
My keyboard now seems to be functioning again.  I checked the bugs on Launchpad and this seems to be a known upstream Gnome bug.  I simply removed the shortcuts on the Rhytmbox-related functions (even though they no longer contained the keys that didn't work) and restarted X, and as long as the Rhythmbox shortcuts aren't assigned to anything my keyboard seems to work.

---

