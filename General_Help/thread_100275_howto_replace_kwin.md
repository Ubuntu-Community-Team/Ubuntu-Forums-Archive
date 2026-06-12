---
title: "howto: replace kwin????"
date: 2005-12-07
forum: General Help
---

### Post by mboto on 2005-12-07
hi there,

i want to replace kwin (if possible) with e16 - also i does not want to miss all that kde features - so what i`d like is to replace just the window manager of kde (kwin - if i am not that wrong).

also i want to run some programms of e 16 like engage...

it may look like this [http://www.elivecd.org/gb/Main/Screenshots/_images/elive-1.jpg](http://www.elivecd.org/gb/Main/Screenshots/_images/elive-1.jpg)
then - but with the possibility to open and close the kde kontroll panel by clicking on the arrow on it (so theres only that button with the orrow on it on the side....)

how can this be done???

i am quite a newbie - so i wanted to ask before i just remove the kwin package with adept and download the e16..

guess that ain`t all the settings i have to do...

does anyone have a clue???

an help would be great

---

### Post by shakin on 2005-12-07
One option is to just run e16 (or e17... ooohhh... aaahhh) and then run 'kicker' from the command line or set it to start on login. This will give you KDE's panel. I think you need to run a different command to start KDE's system tray, but I'm not sure. I think this solution will give you the best performance since you won't load all of KDE. However, there may be some penalty with integration since all of KDE's goodness isn't running in the background. You can check out the contents of /usr/share/autostart to see everything that kde starts and you can manually start what you need, then set them to load upon login.

If you want all of KDE to load, the only way I know how to just swap out kwin for another WM in KDE is to edit /usr/bin/startkde and change the part that starts kwin to start e16/e17. Make a backup of startkde first :)

Anyhow, I'd use my first method to start with because it's easier to reverse... KDE won't be touched in any way.

---

### Post by shakin on 2005-12-07
I should have mentioned that you can run e16/e17 alone, then run kdesktop from the command line. This will load a bunch of KDE stuff such as the desktop with icons. You may have to run kicker separately.

---

### Post by shakin on 2005-12-07
As a test, I just ran 'killall kwin && killall kdesktop && startfluxbox' and it successfully replaced kwin, although I doubt it'll last beyond this one session unless KDE's session manager automates it on startup. It should work equally well for e16/e17.

You can omit killing kdesktop if you still want KDE's desktop menus and icons, but then your replacement WM's menus and desktop items will be lost and it'll only be used to decorate windows along with window behaviours such as focus settings.

---

