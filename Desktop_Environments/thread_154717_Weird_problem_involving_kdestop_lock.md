---
title: "Weird problem involving kdestop_lock"
date: 2006-04-03
forum: Desktop Environments
---

### Post by Princey on 2006-04-03
Over the weekend, I had to end up sharing my home with someone for a few weeks so I started locking my desktop when I moved away from the comp. When I get back to log in, I log in allright after typing my password but then I get the following error "The application unknown (kdesktop_lock) crashed has caused the signal 11 in (SIGSEGV)". Gives more explanation as can be seen in the attached screenshot. Anyone else getting that message? I googled and found that was a bug in kde 3.2 and 3.4 but was since fixed. The bug only shows up when Japeneese fonts are enabled says another bug report filed. I'm not Japaneese and checked to see if anything Japaneese is enabled. No, not one is. I'm using kde 3.52. Any ideas or should I do as it suggests to file a bug report to kde?

---

### Post by devnulljp on 2006-04-05
I have something similar - when I lock the desktop from KDE, it won't let me back in again--my password gets rejected as though the keyboard layout has changed. I've tried typing the password as it would be on various keyboards but still doesn't work. Weird.
I do have Japanese fonts installed though...

---

### Post by Princey on 2006-04-05
[QUOTE=devnulljp]I have something similar - when I lock the desktop from KDE, it won't let me back in again--my password gets rejected as though the keyboard layout has changed. I've tried typing the password as it would be on various keyboards but still doesn't work. Weird.
I do have Japanese fonts installed though...[/QUOTE]

There's a fix for your problem. You can check it out at [http://bugs.kde.org/simple_search.cgi?id=kdesktop_lock]("http://bugs.kde.org/simple_search.cgi?id=kdesktop_lock")

---

