---
title: "Strange mouse/cursor thing going on!"
date: 2005-05-06
forum: Desktop Environments
---

### Post by neilius on 2005-05-06
Hey all, I wonder if anyone else is experiencing this:

The cursor will be the default x cursor when it's meant to be the Kbuntu themed cursor in certain situations, for example:

When i click a link in Konqueror, and its waiting for the page to load so you're meant to see the cursor with the timer next to it, it'll be the default x version of that cursor. Also when i move the cursor over a hyperlink and it turns into the hand with the pointy finger, that's also the incorrect version of that cursor, being the standard x version and not the Kubuntu theme cursor. Is there any way to sort things out so KDE uses the cursors from the Kubuntu theme?

Regards,

Neil.   :)

---

### Post by spookylukey on 2005-05-06
Yeah, I'm getting the same, and also with window resizing cursors.  This one's a real pain, as the center of the cursor is in the wrong place.  I even think this has something to do with a problem I'm having with Win4lin - the hotspot of the mouse cursor is in the wrong place - right from the tip of the cursor by about 8 pixels, which is the same amount the horizontal resize cursors are out by.

---

### Post by spookylukey on 2005-05-18
After installing a different cursor theme (pUbuntu-24 from Pinux to be precise), my problem with the cursor in general is fixed - but I found I had to log out and restart kdm from a virtual console ("sudo /etc/init.d/kdm restart") before it actually got fixed.

With Win4Lin, problem is still ongoing...

---

### Post by deadlands on 2005-05-18
Same for me, until I switched mouse themes.

If you like the Kubuntu mouse theme, use the Jimmac theme from KDE-look

[http://kde-look.org/content/show.php?content=6550](http://kde-look.org/content/show.php?content=6550)

put the index,theme file and cursors folder into your ~/.icon/default folder and restart X.

---

