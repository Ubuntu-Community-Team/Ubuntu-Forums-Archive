---
title: "kde/openbox. wrong main menu location"
date: 2010-12-22
forum: Desktop Environments
---

### Post by DenisBY on 2010-12-22
After pressing K button menu appears at top of the screen instead of bottom.  Here is my screeenshot.

[   [IMG]http://www.zimagez.com/miniature/screenshot-12222010-125614pm.php[/IMG]]("http://www.zimagez.com/zimage/screenshot-12222010-125614pm.php")
Kubuntu 10.10

I can fix it by removing ~/.kde4/share/config/plasma-desktop* but I have to remove it at each logon. It only works for one session.
[ ]("http://www.zimagez.com/zimage/screenshot-12222010-125614pm.php")

---

### Post by sgadecki on 2011-07-14
I'm having the same problem with Kubuntu 11.04.  Installed it over Lubuntu 11.04.  If I use KDE Plasma Desktop the menus are in the right place, however if I use KDE/OpenBox the menus are off the top edge of the screen.  I'm still googling for a solution, but figured I'd bump this thread in hopes that somebody might have a quick fix.

---

### Post by FlappySocks on 2011-07-15
Same problem here. :(  Feels like I have been googling for an eternity.

---

### Post by dabl on 2011-07-15
I don't know "open box", but somewhere, in the upper right corner, or at the right end of the panel, or by right-clicking on the "K", there should be a place where you can "unlock widgets".  Once you do that, right-click on the panel, choose "panel options", and there choose "panel settings".  That should open a large bar where you can find handles to drag the panel to whichever side of the screen you want.  When you have it where you want it, close the settings bar, then "lock widgets" and it should stay there through a reboot.

---

### Post by FlappySocks on 2011-07-15
Thanks, but unfortunately this does not work.

This is the second PC I have had this problem with.  What I normally do, is go into systemsettings >> Default Applications >> Window Managers, and switch it to KDE, apply/accept, and then switch back again to Openbox. A pain, but works until the next reboot.

---

### Post by rganesh27 on 2011-09-01
I had the same problem 


..until a few minutes back ;)

i had started seeing the problem ever since i meddled with the panel..adding and deleting widgets ( in an attempt to get rid of the panel totally..; but wanted the K menu; clock; system tray to be on top of other applications )..:confused:..couldnt do it and hence tried to revert back to the original panel..the position of the notifications..menu etc appeard at the top, and each time i had to adjust the position manually with the panel tool box!!](*,)

I tried altering the display resolution to 1024 X 768 (from my 1280 X 800) ..and moved that toolbox icon ( a golden bean shaped icon) from the top right corner to the top left corner...im not sure which action helped..but the settings are permanent now and the menu and notifications appear correctly! :)

---

### Post by sonic042 on 2011-09-16
I have encountered the same problem and googled, then found a workaround.

> 1. Change your default login to the standard KDE session (kwin)
2. Put an executable script in ~/.kde/Autostart like the following:

```
#!/bin/bash

openbox --replace &
```

3. log in like normal.

 The original post is the 8th post in the following thread in openSUSE forum.
_[KDE/Openbox plasmoid offset off screen]("http://forums.opensuse.org/english/get-technical-help-here/applications/450749-kde-openbox-plasmoid-offset-off-screen.html")_

---

