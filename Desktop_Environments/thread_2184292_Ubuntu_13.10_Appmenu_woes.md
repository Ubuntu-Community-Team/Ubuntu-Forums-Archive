---
title: "Ubuntu 13.10 Appmenu woes"
date: 2013-10-28
forum: Desktop Environments
---

### Post by El Zoido on 2013-10-28
Hello all!

I recently upgraded to 13.10 64bit and discovered some issues with the appmenu ("global menu").
Last version I used was 12.04, where I had uninstalled it completely - I'm not really a big fan of the appmenu, since I believe that on large monitors it's main contribution to usability is to increase mouse travel.
However, on 13.10 I ran into some issues:
1) Nautilus/Files (whatever it is called now) has no menu at all when I remove the appmenu packages.
2) I actually like the idea of entering commands via the HUD on pressing "alt", but that only works with appmenu

I did some searching around and found that apparently it was possible to make a program use both the native menu and the appmenu by starting it with "APPMENU_DISPLAY_BOTH=1 name".
This looked pretty much like the perfect solution for me - I would have both the native menu in the window for convenience and the working HUD commands for even more convenience. Unfortunately it seems that "APPMENU_DISPLAY_BOTH" doesn't seem to work anymore in 13.10. At least it doesn't do anything when starting a programm with the command.

Does anyone know if it is possible to get something like that working, i.e. having BOTH appmenu and native menus for programs?

---

### Post by stinkeye on 2013-10-28
_[http://www.webupd8.org/2013/02/how-to-disable-gnome-shell-appmenu.html](http://www.webupd8.org/2013/02/how-to-disable-gnome-shell-appmenu.html)_

---

### Post by El Zoido on 2013-10-28
Ah, cool! I guess this will at least help me to disable it completely. Thanks!

I would still be interested in a solution that displays it both in the appmenu and the window, though, if that is even possible.

---

