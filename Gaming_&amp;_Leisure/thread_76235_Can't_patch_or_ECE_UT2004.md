---
title: "Can't patch or ECE UT2004"
date: 2005-10-14
forum: Gaming &amp; Leisure
---

### Post by Curlydave on 2005-10-14
I just got UT2k4 set up on breezy and have the ece bonus pack and patch. I opened them up in a root browser, and went to unzip them into the ut2k4 folder. It appears to unzip ok, but at the end of both of them it says error overwriting to folder:X for all of the folders, and they end up not installed. What's up? I can't play online without these.

Here's what it looks like: 

> mv: cannot overwrite directory `/usr/local/games/ut2004/Textures'
mv: cannot overwrite directory `/usr/local/games/ut2004/System'
mv: cannot overwrite directory `/usr/local/games/ut2004/StaticMeshes'
mv: cannot overwrite directory `/usr/local/games/ut2004/Sounds'
mv: cannot overwrite directory `/usr/local/games/ut2004/Maps'
mv: cannot overwrite directory `/usr/local/games/ut2004/Manual'
mv: cannot overwrite directory `/usr/local/games/ut2004/Help'
mv: cannot overwrite directory `/usr/local/games/ut2004/Animations'


---

### Post by Harleen on 2005-10-14
It seems you don't have write privileges on these files. Usually only root is allowed to write outside /home. So you should simply prepend 'sudo' before your unzip command.

---

### Post by xeta on 2005-10-15
Curly please let us know if this is working for you now. (It helps people find fixed)

---

### Post by Curlydave on 2005-10-15
I didn't use a command. I used Archive Manager run from a roote browser.

---

### Post by Harleen on 2005-10-16
I don't know this archive manager, but if it was running as root this should have worked. Maybe you should extract the files to a folder in your home directory first and copy them manually as root afterwards. That shouldn't make any difference, but you may see a more useful message, why the copy fails.

---

### Post by Curlydave on 2005-10-16
[QUOTE=Harleen]I don't know this archive manager, but if it was running as root this should have worked. Maybe you should extract the files to a folder in your home directory first and copy them manually as root afterwards. That shouldn't make any difference, but you may see a more useful message, why the copy fails.[/QUOTE]

That would probably work, but it's a pain in the ass sorta. I guess I'll have to do that.

---

