---
title: "Can't change mouse speed in GUI control."
date: 2006-06-20
forum: Desktop Environments
---

### Post by Rebajas on 2006-06-20
Hiya,

Having recently updated to Dapper I notice the mouse speed has increased. I opened the GUI mouse control from Preferences and adjusted it but now the mouse speed is very slow and my attempts to move the slider back up towards the middle don't seem to save or make any difference.

Is there a text file somewhere I can edit to fix this issue? And what value range does this file accept?

Cheers.

---

### Post by Haegin on 2006-06-21
EDIT: I found a fix.
From a terminal open up gconf-editor
Go into desktop>gnome>peripherals>mouse and set acceleration to 1

Much nicer now but I'm wondering how brilliant dapper is. It doesn't seem any more stable than breezy was when it first came out. Maybe they should have delayed it longer. After all - there's no point getting it now if it doesn't work until august.

Same here - any fix?

---

### Post by Rebajas on 2006-06-21
Cheers for the follow-up. I'm away at the moment but I will give it a go when I next see home.

I agree about Dapper - I haven't had much luck with it yet and desperately hate the new alert boxes, what was wrong with the nice Breezy ones?!

Anyway - I'll persevere and hopefully things will improve (OR I'll end up modifying things myself).

Thanks again.

---

### Post by Haegin on 2006-06-21
I think this is part of a bigger problem with gnome-schemas introduced in an upgrade. Here is a full fix if you have other problems as well.
[http://ubuntuforums.org/showpost.php?p=1164346&postcount=11](http://ubuntuforums.org/showpost.php?p=1164346&postcount=11)

---

### Post by Rebajas on 2006-06-24
That worked a treat - now I don't have to move my mouse the length of my desktop to, err, move the length of my desktop.

I'm sure you know what I mean... :)

---

