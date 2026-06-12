---
title: "What does this terminal output mean?  (Involving Compiz and Emerald)"
date: 2007-08-31
forum: Desktop Effects &amp; Customization
---

### Post by A Whale Of A Time on 2007-08-31
When I type in "emerald --replace" i get this:

liam@liam-laptop:~$ emerald --replace

(emerald:18798): Wnck-WARNING **: Unhandled action type (nil)
(That repeats about 19 more times.)

When I type in "compiz --replace" I get this:

liam@liam-laptop:~$ compiz --replace
core, ccp, clone, zoom, dbus, regex, place, minimize, png, workarounds, move, resize, decoration, wobbly, fade, cube, scale, rotate, switcher, done
A handler is already registered for the path starting with path[0] = "org"

(That last line repeats many more times)


Compiz and Emerald both work after I enter in those commands.  However, if I close the terminal windows that I have entered those commands into the borders of all windows disappear.

WTF?  Any help would be greatly appreciated.

---

### Post by A Whale Of A Time on 2007-08-31
Also, how do I post the output from my terminal into those neat little boxes that everyone else has?

---

### Post by cudaman73 on 2007-08-31
wrap the output you want to see in the boxes with [ code] [ /code]. without the spaces of course.

try hitting alt-f2 to start compiz and emerald, that way you don't have to leave the terminal window open.

as far as the output.... I wouldn't worry about it too much, you said that both work properly, right?

---

### Post by A Whale Of A Time on 2007-08-31
I used alt-f2 to run Compiz and that enabled Compiz to function without a terminal window open.  When I tried the same with Emerald nothing happened.  Any ideas as to what's going on?

---

### Post by Tiger-Smith on 2007-08-31
The reason everything goes when you close the terminal is that your desktop effects are running of that paticular terminal, always use Alt+F2, unless your debugging issues for launching programs.

---

### Post by A Whale Of A Time on 2007-08-31
Thanks for your help.  I solved the problem.

---

