---
title: "gnome-panel locks up"
date: 2008-01-19
forum: Desktop Environments
---

### Post by lvm on 2008-01-19
On a fresh install of ubuntu gutsy x86_64 desktop panels frequently stop reacting while gnome-panel maxes out the CPU and slowly eats up memory. When killed it restarts and works fine for some time, then all is repeated again - sometimes just after several seconds, sometimes after hours but typically I have to restart it every 15-20 minutes which is a damn nuisance. I was not able to pinpoint any particular action which triggers this glitch - sometimes it happens in panel menus, I remember that I managed to add keyboard indicator applet only after the third attempt - twice it locked up in applets list, sometimes I just notice that computer became sluggish and when I move mouse to a panel it won't react, but as far as I can tell it always happens when I am doing something with a desktop, not completely by itself.

My panel layout is not a standard one: taskbar panel is at the left, extended, hiding, Launchpad (or whatever it is called - the thingy  where the update icon pops up) panel is at the bottom, not extended, hiding. Nothing is changed on a background tab. When I set panels back to standard top/bottom extended not hiding layout I didn't have this problem for the half an hour I was able to bear such an uncomfortable layout and such an unproductive waste of screen space, so maybe my panel layout has something to do with the problem, but it is not conclusive and I would definitely not consider an advice to switch back to the standard layout as an acceptable fix.

I did some changes to launchpad panel but not a lot - replaced firefox with seamonkey, added keyboard indicator, tailored menus a but, but as far as I can remember this problem started before that. No new panels.

Less annoying/avoidable bugs/inadequacies: 

1. when an unextended horizontal panel is moved to left/right via the properties-orientation dialog, it changes orientation to vertical but remains in the center of the screen, only extended panels are moved properly - again a sign that unextended panel support is not tested very well

2. when a panel hides it still leaves out an edge several pixels wide which cannot be used by maximized windows and remains on top of windows resized manually, instead of hiding completely an reacting to the mouse being moved to the very edge of the screen

3. on a vertical launchpad panel text is printed sideways, 2d level menus are ok

4. taskbar panel cannot be configured not to show icons, even worse vertical taskbar shows only icons

ps For the last ten years I've been earning my crackers and cheese by unix programming but somehow managed to avoid X exposure till now, so I am a complete newbie in X, gnome and all that - sorry if I use wrong terminology or if my questions are plain stupid.

---

