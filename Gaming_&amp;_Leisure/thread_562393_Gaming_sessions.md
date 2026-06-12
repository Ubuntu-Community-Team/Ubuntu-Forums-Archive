---
title: "Gaming sessions"
date: 2007-09-28
forum: Gaming &amp; Leisure
---

### Post by happysmileman on 2007-09-28
I'd like to know has anyone though of setting up a session in KDM/GDM for a game and how easy it would be to do.

What I'm thinking of is this:

When you want to play a game, you log in, it loads up GNOME/KDE/XFCE and then you open up the game, using your shortcut or the menu or whatever.
However with session entries in KDM/GDM it should be possible to select for example a "True Combat Elite" session, that when you log in, it will start X without a DE and load True Combat Elite, then upon exiting True Combat Elite it will log you out.

This idea would save a lot of RAM in cases, and it would also free up some CPU cycles, or at the very least speed up startup times for the game.
The session would be completely seperate to your regular KDE/GNOME/XFCE and wouldn' interfere with it.

Is this acceptable, am I missing out on some details? Would it even need a Windows Manager, and if so what is the smallest one you could get?

---

### Post by cogadh on 2007-09-28
A lot of us already do something like this when running games with Wine and I don't see why it souldn't work with native games as well. I'm not sure how you could set up a session available from the login, but it is very easy to close the current session or log into a console session and launch a game using a script similar to the one I use for Wine games:
```
#!/bin/sh
#uncomment if launching from console session
#sudo /etc/init.d/gdm stop
#KDE use this instead
#sudo /etc/init.d/kdm stop

# Launches a new X session on display 3. If you don't have an Nvidia card
# take out the "& nvidia-settings --load-config-only" part
X :3 -ac & nvidia-settings --load-config-only

# Goto game dir (modify as needed)
cd "$HOME/.wine/drive_c/Program Files/Game/Directory/"

# Forces the system to have a break for 2 seconds, X doesn't launch instantly 
sleep 2

# Launches game (modify as needed)
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Game/Directory/Game.exe"
```

---

