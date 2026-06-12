---
title: "Open Thunar maximized showing only software of a category... possible?"
date: 2008-01-30
forum: Desktop Environments
---

### Post by darkmaster on 2008-01-30
Hallo everyone, this question is basicaly divided in two:

1) Is it possible to upen thunar maximized with a certain terminal command?
2) Is it possible to open thunar pointing at a folder showing only the software of a particular category? For example, is it possible to have thunar open displaying a folder, maximized, showing all the launchers of the applications from a certain category?

For example, can I run a command that opens thunar maximized displaying all of the launchers for the category "Games" ??
Thank you very much :)

---

### Post by jeffus_il on 2008-01-30
In a terminal type > man thunar

---

### Post by darkmaster on 2008-01-30
> **jeffus_il said:**
> In a terminal type

The manual pretty says nothing or almost mothing.. I already tried thunar --help too.
This is not much different.
Are you telling me I have to understand something about URIs? I don't even know what they are but am trying to google for them.... an example?? :(

---

### Post by jeffus_il on 2008-01-30
I didn't see anything about opening maximized but you could do ```
thunar ~/bin
``` or ```
thunar /etc
```
Try them out!

---

### Post by darkmaster on 2008-01-30
Uhm... ok, loooks like I didn't explain well what I need to do...
I can use thunar this way, pretty simple indeed, that was not what I needed.... Ok can run:

thunar /usr/share/applications

to open thunar pointing at the applications folder for example but this will show all of the applications installed in the system. What I need is thunar (or nautilus or whatever) to show only the applications of a certain category! For example, is there, as I said in the example, a way to tell thunar to show me all the applications contained in the "Game" category? Or in the "Utilities", etc.! 
I need it to show all of the apps of a certain category only! And I need to be able to control which category he has to show. It should work somehow like a menù, you know. 

I could create folders containing the various applications of a certain category but should I install new apps, these folders wouldn't be updated... so I need a semantic solution. 
Thanks again! Hope you have an answer to this :)
Any filebrowser able to do it would be appreciated!

---

### Post by jeffus_il on 2008-01-30
Thunar browses the file system and like any file system browser will show you files and folders. If you want to tailor the menu go ahead and do it.

---

### Post by k7my on 2008-01-30
You can try The Launcher ([http://www.alte.ru/thelauncher/](http://www.alte.ru/thelauncher/)) and/or Xffm ([http://xffm.sourceforge.net/](http://xffm.sourceforge.net/)) inside got a xffm-applications browser.

---

### Post by darkmaster on 2008-01-30
> **k7my said:**
> You can try The Launcher ([http://www.alte.ru/thelauncher/](http://www.alte.ru/thelauncher/)) and/or Xffm ([http://xffm.sourceforge.net/](http://xffm.sourceforge.net/)) inside got a xffm-applications browser.

Wow the launcher would be perfect and it can even be launched in fullscreeeeeeen! Exactly what I needed but... it cannot be launched with a command-line argument to tell it to directly show only the applications with a "games" search term form example...
I tested it with games, utility, system, preferences, graphics, pretty everything and it is fantastic!!! If only could I tell it to display the apps from a aprticular category from command line.... it would be perfect.
My idea is that when a user clicks on the "Graphics" icon, for example, The Launcher shoudl open displaying all the apps in the Graphics category for the user...

---

