---
title: "gnome busted after icewm install and fiddling"
date: 2008-03-21
forum: Desktop Environments
---

### Post by wiggie on 2008-03-21
I installed IceWM today and after doing some fiddling with it, which I will explain in detail below, my gnome just went crazy, that is the menu bars were replaced by either white bars or weird graphic bars that come from the theme. Either way they are unclickable and the shortcut keys don't work either.

This is what I did:
Installed icewm like this:
sudo apt-get install icewm icepref iceme rox-filer xscreensaver ivman

then I realized that icepref doesn't exist / didn't get installed so I downloaded it and installed it, since the font on IceWM was way too small, I logged into gnome to do that and it worked just fine, just like the good old gnome.

After trying to change some stuff with icepref, some of it worked, some didn't, for ex. the font is still small, I installed xfce4-terminal, then I tried to run it, thinking that it would attach to the IceWM terminal. Well it didn't and I think that is where my gnome busted.

I have also loaded rox and ivman on startup through the .icewm/startup file, but I think that shouldn't affect gnome.

After I realized that gnome is busted I tried looking for answers and found some, which I tried. 
For example I removed ubuntu-desktop and reinstalled, but it still didn't work.

What can I do?

wiggie

**EDIT: ** I logged back into gnome, and tried to get to the desktop settings through right click > change desktop background, and a message appeared telling me something about** gnome-desktop-deamon**, that it could not start, and bonobo also had problems, and also that there might be some other something else running that could be accessing the settings, in my case IceWM. I hope this helps you help me ;).

---

