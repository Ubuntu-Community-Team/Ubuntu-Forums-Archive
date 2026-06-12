---
title: "Starting things at login, help"
date: 2007-05-07
forum: Desktop Effects &amp; Customization
---

### Post by searayman on 2007-05-07
When i set beryl-manager and my dock to start up at when i logg in with session manager they see to start really really late, liek a minute or two after i log in. How can i make them start up as soon as i logg in?

---

### Post by LuisGMarine on 2007-05-07
I'm not sure about your dock, but for beryl this is what I did.  Keep in note that if you start your docks with a simple command like you do for beryl, then I don't see why this might not work for it.

First go to System > Preferences > Sessions 

Under the 'Startup Programs' tab, click the 'New' button on the right hand side.

When the ' New Startup Program ' comes up, under ' Name' type in Beryl.

Under 'Command' type in:
```
beryl-manager
```

Hit 'OK' and you should be good to go.

=======================================

If its starting too late, in the same window , go to the "Current Session" tab, and look for beryl-manager ( note you would of had to log out and back in for beryl-manager to start by itself )

Once you are in the window, locate beryl-manager and change the order to 45.  Keep in note you don't want to start beryl before any of the gnome stuff gets up because it might cause some problems.  So I usually have it 45 since all my other programs that I choose to startup at the beginning are order at 50.  So 45 is perfect for me.

Good Luck

---

