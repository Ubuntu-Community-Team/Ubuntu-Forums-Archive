---
title: "Why does Nautilus no longer have keyboard shortcuts in 13.04?"
date: 2013-09-28
forum: Desktop Environments
---

### Post by andrewkirk on 2013-09-28
I use Nautilus a lot and instinctively use kbd shortcuts for rapid action. Examples are Alt-B for bookmarks list or Alt-F for File menu. Most of the shortcuts I use are via the standard method of pressing Alt together with the underlined letter in the menu item.  

These are no longer available in the Ubuntu 13.04 File manager, forcing me to reach for my mouse, which is MUCH slower.

Is there any way to get the Alt-related keyboard shortcuts for the Nautilus menu back?

My system is 13.04, upgraded from 12.04, running on an HP EliteBook 2530p (INtel x86 32 bit). The desktop environment is the default from the install, which I am pretty sure is Unity. The file manager calls itself Files 3.6.3 although it looks just like Nautilus except for the lack of useful keyboard shortcuts.

Thank you

---

### Post by mc4man on 2013-09-28
you can take a look in - 
~/.config/nautilus/accels
As far as any edits to that file - may take some experimenting, could be that any edit will need no ; at beginning of edited or added  line 
(or just some??, see here for example where it had to be removed or not included - [http://askubuntu.com/questions/287936/changing-nautilus-key](http://askubuntu.com/questions/287936/changing-nautilus-key)

---

### Post by andrewkirk on 2013-09-28
Thank you mc4man. I did your change and I got back the kbd shortcut for BackSpace to go up one dir.

But so much else of the previously available functionality has been removed (many of the things I used to do like pull up a pop-up list of bookmarks with Alt-B aren't even available as functions to which shortcuts can be assigned any more!) that I've decided to ditch Nautilus in favour of Pcmanfm.

I cannot imagine what the developers were thinking to have ripped out so much of the functionality and usability from Nautilus in this new release, but that's their prerogative so there's no point complaining.

---

