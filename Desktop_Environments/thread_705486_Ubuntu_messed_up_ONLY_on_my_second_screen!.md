---
title: "Ubuntu messed up ONLY on my second screen!"
date: 2008-02-23
forum: Desktop Environments
---

### Post by Triple Omega on 2008-02-23
First of all I'm a complete beginner when it comes to Ubuntu and linux in general. I've only been toying with it for a few weeks.

Today I tried to get my second screen to work as separate screen(not clone or extended). So I sudo'ed into sysinfo, went to the nvidia settings(have a 8800 GTS 640. Just in case it matters) and enabled my second screen as separate screen. I saved the settings and restarted.

No problems booting up or logging in and even my main screen was working without a hitch and all my settings were still good. It's only when I started a program on my second monitor that I noticed a problem.

The edges of windows are gone. By which I mean the outer boundaries of windows. So the terminal for example looks like a white rectangle with a scroll bar at the right and a menu at the top. Nothing more. Even the top edge, with the name of the window and the minimize, maximize, close buttons, is gone.

Does anyone know why this happens? And why it only affects my secondary screen and not my main one? Any help would be appreciated.

---

### Post by Sam Lars on 2008-02-23
I don't know much about separate screens like that, but it sounds like the window decorator isn't started...
Are you using Compiz?  Try running compiz, or, if not, then metacity.

---

