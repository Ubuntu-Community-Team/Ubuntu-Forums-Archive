---
title: "Installed kubuntu-desktop on ubuntu8.10, can't login, installed fluxbox, messed up."
date: 2009-02-17
forum: Desktop Environments
---

### Post by Ubempi on 2009-02-17
After days of searching the Internet and trying, after lots of man pages, I give up...

Here is my situation.

[[img]http://img408.imageshack.us/img408/1361/screenshotsm6.th.png[/img]](http://img408.imageshack.us/img408/1361/screenshotsm6.png)
or go to [http://img408.imageshack.us/img408/1361/screenshotsm6.png](http://img408.imageshack.us/img408/1361/screenshotsm6.png)

Today when I boot my Ubuntu 8.10 installation I get a blank (or so) screen with a terminal (see atachment). This terminal has no borders, that is, there is no window manager running. If I write there "fluxbox" the fluxbox desktop loads very well, same for gnome-session, didn't try (don't know) for kde4.2

This is the history:
-I had a very well working Ubuntu 8.10 desktop with the default gnome. 
-added the repositories for it, and installed kde4.2, that was "xubuntu-desktop".
-Ok, it asked me to choose between gdm and kdm, I choosed gdm.
-every thing was good, I configured gdm to automatically log in with my user, and to automatically log in with kde session.
-So I started to use kde4, but I got realized that the gnome desktop was loading "behind" the kde desktop (could see it when moving from one of the two kde desktops to the other). 
-OK, I said, logout and initiate a session with gnome to see if every thing was ok there, but guess what? 
-On logout, the time it took was very long.
-After logout I couldn't login again (keep showing me the login screen again and again, kdm does the same)
-Had to reboot every time for gdm to autologin to kde4. (or press ctrl+alt+F1 and stop gdm, start gdm)
-Installed fluxbox (maybe this will fix something I thought)
-Ubuntu initiates directly to fluxbox.
-Started to play with man pages, searched the Internet and tried to understand how to configure gdm to start gnome instead of fluxbox. Never could.
-Started to "Start" and "Stop" gdm. Trying things.
-gdm started to complain that it was being killed repeatedly.
-gdm now logs me in automatically but only shows a terminal in the bottom right corner of the screen, with no borders.
- In that terminal I can write "fluxbox" to start fluxbox, "gnome-session" to start gnome, (don't know for kde), and if I do put this commands on that terminal every thing goes well.

:( 

Do I need to format and re-install?
I don't know the contents of witch files should I show you here to diagnostic the problem.

Note that I tried my best before posting, I'm simply tired.

---

### Post by Ubempi on 2009-04-14
Ok. I've fixed something, I don't know what. Just started to play with the window this command shows.

```
gksu /usr/sbin/gdmsetup
```

And the problem of the desktop not loading is gone. I don't actually know if this was the thing that solved the problem... any way :lolflag:

---

