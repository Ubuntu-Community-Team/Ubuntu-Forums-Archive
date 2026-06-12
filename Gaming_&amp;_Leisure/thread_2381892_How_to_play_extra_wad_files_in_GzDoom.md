---
title: "How to play extra wad files in GzDoom"
date: 2018-01-06
forum: Gaming &amp; Leisure
---

### Post by Hewjr100 on 2018-01-06
Does anybody know how to play wad files in gzdoom on Ubuntu 16.04, specifically I am not referring to my original doom wads, but rather some free ones I downloaded from Doom sites.  In windows 10 to play the wad files I have to drag them over Gzdoom.exe, which prompted to run the file with this program.  I do not know how to do this in Ubuntu.   Any help would be appreciated.
 
 
 Henry

---

### Post by deadflowr on 2018-01-06
I think you need to place the wad files (either directly or symlinked) into the config folder at /home/you/.config/gzdoom.

---

### Post by Hewjr100 on 2018-01-06
Absolutely, I did, but in .config/gzdoom the only file that was there, before I copied and pasted wad files was gzdoom.ini   When I run GzDoom it sees the stock wad files:  ie: Doom, Doom 2, Tnt, Plutonia and so on.

Henry

---

### Post by deadflowr on 2018-01-06
These wads run fine in Windows gzdoom?
Or are they new?

Perhaps port/wad/engine compatibility issues?
Or maybe linux port/engine issues?

---

### Post by Hewjr100 on 2018-01-06
Not sure about, I guess if I could find the gzdoom executable and drag the wad files on it, then it either would run or not.

Henry

Look at all these wads.

[ATTACH=CONFIG]278077[/ATTACH]

---

### Post by Holger_Gehrke on 2018-01-07
You can just call it from the shell:
```

gzdoom AbsolutePathAndNameOfTheWADwithExtension

```
gzdoom is a bit peculiar, it won't accept relative pathnames. There is a section [FileSearch.Directories] in ~/.config/gzdoom/gzdoom.ini. Any path in that section will be searched for files if you pass only filenames without path.

To make drag'n'drop possible, you have to change the .desktop file used to start gzdoom which should be /usr/share/applications/gzdoom.desktop. Copy this file to ~/.local/share/applications and open it with your editor of choice. Change the line starting with "Exec" to ''Exec=gzdoom %F". (you could of course also change the original file, but the next update might overwrite your changes).

Holger

---

### Post by Hewjr100 on 2018-01-07
Beautiful, I am very thankful for your help.

Henry

---

