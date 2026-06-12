---
title: "Problem with menu-editor in GNOME"
date: 2005-04-22
forum: Desktop Environments
---

### Post by tirog on 2005-04-22
Hello.

I have a problem with menu-editor in GNOME. When I want save entry, this entry always save in category "Others". If somebody had same problem, I'd want a URL to thread  :-k 

Any ideas?
Thanks.
tirog

---

### Post by coldturkey on 2005-04-22
I've got the same wierd problem, only with NVIDIA Settings though. I've installed DC++  and made an executable from menu-editer, at first it went to Others too but I edit:ed it and it moved to System. But NVIDIA Settings doesn't move...

---

### Post by Suzan on 2005-04-22
Got the same problem - all entries went into "Others".

---

### Post by Loop0nBlue on 2005-04-22
I had the same problem with [color=Red]NVIDIA Settings[/color].
After quite a few headaches, I found that those entries that went to [color=Red]Others[/color] were stored in your home folder, under [color=Blue]/.local/share/applications/[/color]
Deleting the [color=Blue]*.desktop[/color] files that went to [color=Red]Others[/color] completly removes the [color=Red]Others[/color] folder.

But still, the only way to change the entries in the gnome menu was (for me) to edit the [color=Blue]*.desktop[/color] files under [color=Blue]/usr/share/applications/[/color].
Beware that, if not correctly done, it can be really buggy.

---

