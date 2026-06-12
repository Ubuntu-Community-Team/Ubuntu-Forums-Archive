---
title: "kstart and program stuck in fullscreen"
date: 2010-08-06
forum: Desktop Environments
---

### Post by theLured on 2010-08-06
I have a program running everyday at 4pm using kstart
kstart --fullscreen anki

The problem is when I then load it afterwards without the kstart command, the program will still be in fullscreen mode.

How can I turn off fullscreen at the terminal, or make the kstart command temporary?

I already know that pressing alt+F3 will bring up the menu where I can exit fullscreen.

---

### Post by theLured on 2010-08-22
I have solved it now. Thanks to all the replies lol.

Loaded up the program and right clicked on the title bar(or press alt+F3).

Went to Advanced > Special application settings.

Clicked on Geometry tab

Ticked Fullscreen, set the drop down box to "apply initially" and left the check box next to it blank.

The 2nd checkbox will tell kde that I want to load in fullscreen if ticked and windowed if not ticked.

So now when I run anki, it will be in windowed mode and "kstart --fullscreen anki" will load in fullscreen.

---

