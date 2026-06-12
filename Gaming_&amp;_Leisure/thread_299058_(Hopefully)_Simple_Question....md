---
title: "(Hopefully) Simple Question..."
date: 2006-11-13
forum: Gaming &amp; Leisure
---

### Post by kitpierce on 2006-11-13
Just wondering how one would go about resetting the high scores for KDE games.  I am assuming that there's a score file stored somewhere (/usr/share or someplace like that) which if would delete would clear my highscore lists.  But for the life of me I can't find it.

The specific game in question is KNetWalk, although I would like to know for future games as well.  If anyone knows where this is (and possibly what the file extension and/or file name is) I would be most grateful.  Thanks much!

---

### Post by taurus on 2006-11-13
Move to Gaming & Leisure...

---

### Post by hikaricore on 2006-11-13
Most games make a hidden file in your home directory "~" open a terminal and goto your home dir (it should start there by default anyway) and type:

```
ls -a
```

This will display all hidden files.  There may be a config file for KNetWalk called .KNetWalk or a directory of a similar name where the game stores it's configuration and other data.

If not I don't honestly know where to look, kde probably has it's own config file for the whole interface or a series of files you may have to dig through.

Good Luck,

--Aaron

---

### Post by JoeDesertrat on 2011-06-06
Replying so I can find the answer next time I need it! Most of them seem to be in .kde/share/config

---

