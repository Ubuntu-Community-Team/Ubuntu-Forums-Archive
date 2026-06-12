---
title: "windowmaker question"
date: 2006-01-17
forum: Desktop Environments
---

### Post by D1G1T4L on 2006-01-17
i have installed windowmaker but when i left click, the application window is all empty, how can add some apps to application? or how do i restore the ones from gnome to my application bar


i used wmconf utility or something like that under gnome, and it said it couldnt add my applications

can anyone help

---

### Post by briancurtin on 2006-01-17
i actually was wondering the same thing myself, as i started dabbling in WM myself and id like to start using it a lot more

one day it switched from displaying a very limited selection, to being the Debian menu that i have in GNOME, listing basically everything ever. i havent tried it since the day that happened, so maybe it still does that, but id like to be sure that there is a way to add to the application window just like you

---

### Post by D1G1T4L on 2006-01-17
also my screen gets weird lines osmetimes and i dont see anything (maybe cause my video card is old, but it displays gnome normaly)

what is another alternative to windowmaker that i can use with dockable apps etc

---

### Post by Iesos on 2006-01-20
I know how to fix the empty applications menu. All you need to do is to type:
$ rm -Rf ~/GNUstep/Defaults
This will wipe out some of the preferences you have made during your first use, but when you start WM again, the applications menu will be restored.
I think you have to do this when WM is shut off. In gnome or KDE or in some of the tty-terminals (press Ctrl+Alt+F1 -6) before you log on.
I don't take any responsibility for any loss of information. But I can assure you that it works. I did the same mistake yesterday and I wiped that catalogu, and everything works fine.
In the future, stay away from pressing any yes buttons in the preferece menu that you dont know the consecuences of. (Thats where I messed up).

If some WM user reads this and wants to help me out, please take a look at:
[http://www.ubuntuforums.org/showthread.php?t=119590](http://www.ubuntuforums.org/showthread.php?t=119590)

Well, good luck and sorry for my bad english.

---

