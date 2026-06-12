---
title: "[SOLVED] Emerald problem"
date: 2007-11-08
forum: Desktop Environments
---

### Post by S3loth on 2007-11-08
I just installed a new emerald theme, but it wouldn't work, so i used emerald --replace and it changed it, but when I closed out of terminal, it deleted my top window bar. How do I get the theme to work, or at least get back my window bar?

---

### Post by mcduck on 2007-11-08
If you start a program from a terminal and you close the terminal the program will close as well.

Just press Alt-F2 to open the Run Command-dialog and run the 'emerald --replace' from there.

OR if you want to do it froma terminal, use following command: 'nohup emerald --replace &'. Nohup will allow the program to detach itself from the teminal so it won't close if the terminal is closed, and the '&' at the end will make the command to run on background, leaving the terminal window usable for other tasks.

---

### Post by atomkarinca on 2007-11-08
to get your old window decorations just hit alt+f2 and type

> gtk-window-decorator --replace

or if you want the emerald as your decorator then again hit alt+f2 and type

> emerald --replace

or if you want to use the terminal then with the same commands with just one difference:

> emerald --replace &

or

> gtk-window-decorator --replace &

edit: i'm just a slowpoke, i guess :)

---

### Post by S3loth on 2007-11-08
Still no luck, the top of all my programs are still cut off, even when I try to undo it. When I put in gtk-window-decorator --replace in alt+f2 the windows seem to "jump" up, then back down, but nothing happens.

Edit: All right, somehow its working now, so thanks.

---

