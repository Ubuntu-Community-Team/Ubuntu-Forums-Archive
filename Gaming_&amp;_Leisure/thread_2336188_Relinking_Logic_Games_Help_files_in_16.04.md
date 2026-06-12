---
title: "Relinking Logic Games Help files in 16.04"
date: 2016-09-05
forum: Gaming &amp; Leisure
---

### Post by jeofva2 on 2016-09-05
Forgive me, but I am very new to Linux and would like some help with what is probably a fairly simple problem. 

It appears to me that this question has not been answered, but I could be wrong.  If I am wrong, please direct me to the answer - I couldn't find one.

One  of the many problems that cropped up when I "upgraded" from 14.04 LTS  to 16.04 was that I lost all help for the embedded games - in particular  the "Logic" games.  When I click on the "Help" link for one of the Logic games I am  presented with a blank help window.  I am assuming that the problem is  that the "help" link is looking for the help files somewhere that they aren't.  I hunted around and did find the help files, but can only bring  them up in browser (they are all html-type files).   That address is:
```
//usr/share/sgt-puzzles/help/en/d*ocindex.html
```

The puzzles them selves are located in:
```
// usr/games
```

I don't know what the best course of action is, but it does seem that I need to find out where the game files think their help files are located. I don't know if the location string of the help files for each of the games are hard-coded  in each the game files, or if the directory for the files are stored in some INI-like  file.  

Any help would be greatly appreciated.

---

### Post by irv on 2016-09-05
Did you try reinstalling the game. If that doesn't work just try completely removing it and then reinstalling it.

---

