---
title: "Gnome Panel Applet for Closing Active Window?"
date: 2006-01-07
forum: Desktop Environments
---

### Post by Greg T. on 2006-01-07
I'd like to see a Gnome panel applet that, when clicked, closes the active window. I'd like to put the applet in the right-hand corner of the top panel. This way, when I want to close the active window I'd simply throw my mouse to the upper right-hand corner of the screen, rather than aiming for the window's close button. (In other words, this would be an application of [Fitt's Law]("http://www.asktog.com/basics/firstPrinciples.html").) 

The problem is, with my limited hacking skills I haven't found a way of doing this. I know there is a keyboard binding in metacity (<alt>F4) that closes the active window, but I haven't been able to find an easy way to invoke this functionality through code. Ideas, anyone?

---

### Post by 23meg on 2006-12-24
You can use wmctrl to do this. Put the following into an empty file```
wmctrl -c :ACTIVE:
``` make the file executable and put a launcher that points to it on your panel.

---

