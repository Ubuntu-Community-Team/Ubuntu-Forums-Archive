---
title: "wine windows are grey and won't let me select files"
date: 2006-10-17
forum: Gaming &amp; Leisure
---

### Post by glassgloss on 2006-10-17
I am using wine to play EV Nova, an old game--however, when I use wine to navigate around with i.e. to "open" a file the window is gray, has no selection portion, and when I click the dropdown menu, there are no subfolders.

any ideas?

using the latest version of wine

---

### Post by glassgloss on 2006-10-18
:)  do you need any extra info?

---

### Post by hikaricore on 2006-10-19
Depending on how old the game is, you may need to adjust wine through (from command line):

```
winecfg
```

On the Applications tab you can change the windows version to match the version the program was designed for, that may help a little bit.  I had to do this for my castle of the winds games to be able to open saved games.  You might also check to make sure you have some drives mapped in the Drives tab, the game might not see any drives set and that could have the effect you mentioned.  Exactly what kind of files are you trying to open?  saved games or data files or what?  If all else fails you may have to make launchers to open whatever files you need in the game.  Example:

```
wine z:\gamedir\game.exe gamefile.example
```

---

