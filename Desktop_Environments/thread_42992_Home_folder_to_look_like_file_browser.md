---
title: "Home folder to look like file browser"
date: 2005-06-20
forum: Desktop Environments
---

### Post by Holdem on 2005-06-20
Under Places the Home folder looks like this:
[img]http://xs34.xs.to/pics/05251/home.png[/img]

But I want it to look like my File Browser under Aplication>System Tools
[img]http://xs34.xs.to/pics/05251/File_Browser.png[/img]

I've tried all the settings I can think of but to no avail. Does anyone know how to get the Home folder set to the same view as my File Browser folder?

---

### Post by mike998 on 2005-06-20
Gconf Editor > Apps > Nautilus > Preferences
Check the "Always Use Browser" option.

---

### Post by lorenzo on 2005-06-20
I made a desktop launcher icon with the command

"nautilus --browser /home/memyself/"

I don't know, however, how to change the "Places" launcher...

---

### Post by Holdem on 2005-06-20
[QUOTE=mike998]Gconf Editor > Apps > Nautilus > Preferences
Check the "Always Use Browser" option.[/QUOTE]

Bingo!

Thanks.

---

