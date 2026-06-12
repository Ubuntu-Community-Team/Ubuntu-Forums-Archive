---
title: "Desktop won't load after login"
date: 2006-04-03
forum: Desktop Environments
---

### Post by bikeboy on 2006-04-03
Hey guys got a problem on my Ubuntu lappy.

Yesterday I tried to open a wmv file and the whole computer froze, could not ctrl+alt+backspace or ctrl+alt+f1 or anything so I had to do a hard power off. This has happened once or twice before and all has been fine on restart.

This time, I get to the GDM login, enter my details and the screen changes to the plain colour screen to start loading the desktop. Problem is it stops there, no HDD activity, mouse works but nothing to click. The splash screen doesn't even come up. Same deal if I try the failsafe Gnome session.

I can get to another tty from using CTL+ALT+F1 and have tried restarting gdm and X, looked through logs etc but can't find the problem. Someone on another forum suggested creating a new user to see if it worked for that user and it does. It must be something in my home directory settings that is causing it to not load gnome fully.

Any ideas???

ps. I hadn't edited any config files etc during that session before it froze, just checked email and a few other web things that's all.

---

### Post by Phlosten on 2006-04-04
Perhaps your X server config file is stuffed?

Might be worth running 'sudo dpkg-reconfigure xserver-xorg' just to make sure that is fine.

---

