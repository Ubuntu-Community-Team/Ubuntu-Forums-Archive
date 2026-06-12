---
title: "Lost all destop functionality"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Kepler on 2006-08-03
I can log into my user account and my desktop wallpaper appears but that's about it.  There are black strips where my toolbars should be but no functionality of any kind.  It doesn't appear that Metacity, Nautalis, etc... are loading after I log in -- no splash screen appears before the desktop appears.  Luckily my emergency account still functions but I would prefer to recover my existing 'broken' account rather than start all over.  Granted, option 'B' might be faster but this is strange enough to have piqued my curiosity.

Any ideas on what might've happened to cause this and/or what I might do to fix it?

---

### Post by sulobanks on 2006-08-03
I suppose the first place I'd look is recently installed software, especially third party stuff you install in your home directory somewhere.  Next, I'd look to themes.  I've had a bad theme completely wreck my desktop before, although that was a long time ago.  Maybe replacing your .gtkrc file with the default one would make it possible to log in correctly.

---

### Post by Kepler on 2006-08-03
Bingo!  Copied a 'known good' .gtkrc file into the broken account's home directory and recovered access to the desktop.


Note to self: Inquire into use and importance of .gtkrc file.  :-D 


Thanks Much!

---

