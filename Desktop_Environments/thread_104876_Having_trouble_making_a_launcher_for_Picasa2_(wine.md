---
title: "Having trouble making a launcher for Picasa2 (wine)"
date: 2005-12-17
forum: Desktop Environments
---

### Post by spaceballl on 2005-12-17
Does anyone have some advice for me? I've set up a username on this computer for my mother and I have nice icons for all of the basic programs like Amarok and Openoffice. I found F-Spot MUCH MUCH less user friendly than iPhoto (what my mom is used to) so i went w/ Picasa). It works great! However, how do I make a launcher for it? I made one by using the right click command on the desktop and the only thing I did was under name, I wrote "picasa" and for command I wrote "wine /directory/Picasa2.exe" and that didn't work for me. If I run it from the command line once i'm in the picasa directory though, works like  charm. Any help would be greatly appreciated!

---

### Post by kosmic on 2005-12-17
It should be like this :
 
wine "/directory/Picasa2.exe"

---

### Post by spaceballl on 2005-12-17
Thx!

---

### Post by eneth80 on 2006-12-07
> **spaceballl said:**
> Thx!

Hi, I have a problem with a launcher for a nice dictionary i have (Huygens). From the terminal it works with:
wine /home/username/Desktop/huygens/Huygens.exe

from the launcher i type in the Command blanks:
wine "/home/username/Desktop/huygens/Huygens"
and a window of the dictionary appears, with written in dutch that I cannot open the bloody dictionary. do you have any suggestion?
note that this other dictionary works well from the shortcut as well:
wine  "/home/username/.wine/drive_c/Program Files/Zane Publishing/MW Dictionary-Thesaurus/DictionaryThesaurus.EXE"

thanks
eneth80

---

