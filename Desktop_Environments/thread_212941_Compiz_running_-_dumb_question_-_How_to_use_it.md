---
title: "Compiz running - dumb question - How to use it?"
date: 2006-07-10
forum: Desktop Environments
---

### Post by sup on 2006-07-10
So I installed xgl and compiz with help of excelent wiki pages and it seems to be running. But how do I actually use it - I mean, how do I make the cube and other cool stuff we all have seen on those videos? Only change I have noticed so far is that it is impossible to minimize/quit/etc windows with hitting buttons in top right corner of windows because those buttons arent even there! SO i switched back to good old metacity, but I am still interested in the cube!

I thought it had something to do with workspace switching, but workspace switcher seems to be unoperationable, so it maybe means compiz is broken? Or does it?

I know this may seem dumb but there is so much stuff about gettind it run that I could not find anything about actually using it.

---

### Post by mostwanted on 2006-07-10
Click on one of your virtual desktops (lower right corner) or press alt+ctrl+arrow or alt+ctrl+shift+arrow (moves window as well). To do a "free cube" press alt+ctrl and hold down your left mouse button while moving the mouse.

To peek you just drag a corner of a maximised app.

F12 or F10 does the exposé effect.

---

### Post by irfrausto on 2006-07-10
Did you get the packages from Quinn's repos? The ones in the Dapper repos are old and broken. I believe the window manager is broken in the old packages which is why you can't see the window buttons.

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

Put that in your sources.list and sudo apt-get update, then sudo apt-get upgrade. Install all of the updates, restart GDM (assuming you have done all the config stuff to xorg beforehand, which if you have gotten this far I assume you have) and you should be good to go.

---

### Post by sup on 2006-07-10
My bad, something must have been bad with my compiz session, now that  I fired it up (well first xgl froze so I had to reboot, then it did not come up for the first time but just for the second, ehm) with 
```
gnome-window-decorator &
compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher trailfocus water bs neg &
```, effects were obvious, just opening a menu made me dizzy. I now can see why there are no articles on using it - it is really obvious when it is running properly. Too bad it died after five minutes when I tried to run a movie in fullscreen. 
I think I will turn off most of the effects anyway once I start using it on regular basis - which will not be any time soon since it still seems to be really buggy.

---

