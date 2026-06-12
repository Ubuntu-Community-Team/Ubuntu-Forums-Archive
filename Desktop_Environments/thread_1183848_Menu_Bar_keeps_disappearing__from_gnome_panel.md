---
title: "Menu Bar keeps disappearing  from gnome panel"
date: 2009-06-10
forum: Desktop Environments
---

### Post by netJackDaw on 2009-06-10
I don't know what I did but suddenly my Menu Bar and my custom panel launchers disappeared from the top (default) gnome panel. If someone knows how this can happen, enlighten me!

However I thought it would be easy to just restore the items by right clicking and use Add to panel... I can add a new Menu Bar but when i log out and back in again it is disappeared again. I've tried this quite a few times and I can't get it to stick. I even tried to remove the old panel and replace it with a new one. Same problem....

Please help me with this, its not fun anymore...

---

### Post by miniyak on 2009-06-10
i have a similar problem. Except instead of the menu bar my Network and original power management icons disappeared. I can get a power management tray on there but it is different then the original and fails to update itself on AC/battery events, so i want the original one back

---

### Post by netJackDaw on 2009-06-10
Hello! Solved the problem! It turned out that the file .gconf/apps/panel/%gconf.xml was damaged so the system could not write to it. Tried to remove the file but I got an error like: stale nfs handle. Probably this was due to an unclean shutdown earlier...

I had to restart the machine and log in to recovery console, select fsck to repair the file system. Success this time, held my breath for a while there...

---

### Post by miniyak on 2009-06-10
how did you know to look there? just curious

where did you find that file at? i did a search with no luck

---

### Post by netJackDaw on 2009-06-10
I searched like a maniac on Google and found an article describing how to restore the gnome-panels: [http://lists.ethernal.org/oldarchives/cantlug-0610/msg00566.html](http://lists.ethernal.org/oldarchives/cantlug-0610/msg00566.html) which I thought would help my case.

It was when I tried to follow the instructions that I got an error message. Took it from there...

Maybe you shold look in to that article too...

---

