---
title: "My panels are f*ed"
date: 2010-04-23
forum: Desktop Environments
---

### Post by PfromD on 2010-04-23
This is what I did:
I thought I'd set the task panel at the top of the screen with no auto-hide, and the 'main' panel also at the of the screen, but in auto-hide, for the effect of the open windows always being visible on one panel, and the panel with the program menu popping down below it. That didn't work out as intended.
Result: some kind of bad loop. 

I.e when clicking the visible panel (not even sure which of the two it actually is) to undo the placement at the top for one of the panels, everything goes coma.
Well, I can ctrl-alt-del close/restart the computer, but I'm being informed that "panel" isn't responding. duh! you don't say?!
Any suggestion on fixing this is highly appreciated.

Isn't it a bit of an error that that the top of the desktop isn't being reset as the bottom of the fixed panel at the top of the screen? The one panel would like to pop out on top or underneath the other that is fixed, and that makes it all go ... well, coma.

---

### Post by 2hot6ft2 on 2010-04-23
You could reset the panels to their default.
Use Alt+F2
and follow these instructions (**be very careful with the second one**)
> **lidex said:**
> Terminal:
```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by mattro200 on 2010-04-24
I also messed up my panels trying to play around with an XP look. 

Thanks for the tip, all is back to normal.

---

### Post by 2hot6ft2 on 2010-04-24
You're welcome. You may want to keep those commands handy if you're going to keep playing with them.
Here's you some more to play with.
[http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html](http://www.ubuntugeek.com/howto-make-ubuntu-look-like-windows-vista.html)
-------
[http://www.hackourlives.com/?p=1258](http://www.hackourlives.com/?p=1258)
-------
Win 7 snap windows
[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

And one I did on a flash drive.

---

### Post by drreed on 2010-04-24
You can usually right-click on one of them and change it's width to 'normal' - that will allow you to see whats behind it. Also note that it's possible to right click on one panel, yet access the other one from the same dialog by choosing 'panel 2' for example, in the drop down panel-selector control.

---

