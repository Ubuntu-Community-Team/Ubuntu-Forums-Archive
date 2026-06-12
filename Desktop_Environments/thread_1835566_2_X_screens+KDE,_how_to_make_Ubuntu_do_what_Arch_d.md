---
title: "2 X screens+KDE, how to make Ubuntu do what Arch does."
date: 2011-08-29
forum: Desktop Environments
---

### Post by thegoonden on 2011-08-29
I was playing with Arch a bit last week, and while doing so I set it's X server to "2 separate X screens" for my two monitors, just to test how that worked (my Ubuntu was in non-dynamic twinview at the time).
 When I ran KDE in that configuration, I could place plasma widgets on either screen, and KDE's window manager handled....well...window management, on both screens no problem at all.
I set Ubuntu up the same way (first by hand and later by copying the xorg.conf from Arch to Ubuntu)......but there is no window manager on the secondary display.

Some googling reveals that this is how it's meant to be, and I had to spawn IceWm on the secondary display in order to get window borders etc.


The thing is, I now KNOW it can work properly.
Does anyone have any idea how I can get KDE to manage windows on both screens under Ubuntu? Or where the  behaviour is defined so I can rob the settings from Arch and apply them to Ubuntu?

It really was an almost ideal setup (twin view disables all the cool 3d and transparency stuff, but having an alien window manager on one screen kills it there too.


Thoughts?

(must say though, I may end up sticking with Arch until Ubuntu fixes the "no vsync" issue....hopefully in the next release......at least for watching videos)

---

