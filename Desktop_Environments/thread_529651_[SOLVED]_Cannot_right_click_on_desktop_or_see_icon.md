---
title: "[SOLVED] Cannot right click on desktop or see icons/folder on desktop"
date: 2007-08-19
forum: Desktop Environments
---

### Post by Flak Monkey on 2007-08-19
A friend was on my computer recently and he decided to dedicate his time, while I was away, to screwing up as many things as possible. Luckily, he doesn't really know right from left on a linux box so I was able to get things back in order pretty quickly. However, I still can't right click on my desktop or view the folders or icon in the directory. I've restarted, restarted X, tried switching window managers, made sure show desktop and icons was on, but I still cant fix the problem.

Thanks for the help!

---

### Post by Happy_Man on 2007-08-19
Open up gconf and navigate to apps/nautilus/desktop and make sure everything you want is checked. That should perhaps take care of your icons..... not sure about the right-click.

---

### Post by sabrewolf2006 on 2007-08-19
Could we have more information.. What's the systems current state?
What are using,
WM? (I have experienced a problem like this with an old build of Beryl but since you said you've changed your WM)
GNOME?
KDE? (May not be able to help with this one)
Is nautilus controlling the background?
If it isn't, start it and go into Sessions (Under Preferences) and set its state back to restart..

---

### Post by Flak Monkey on 2007-08-19
Fixed the problem, there were some compiz fusion updates today and I installed those and restarted X and everything was fine. Thanks anyway guys.

For refrence:

Happy_Man: I had already tried to the gconf route but that was a no go.

sabrewold: I'm using compiz-fusion with nautilus controlling the wallpaper and my sessions was good.

---

