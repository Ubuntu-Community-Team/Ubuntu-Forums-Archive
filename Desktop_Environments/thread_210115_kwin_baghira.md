---
title: "kwin baghira"
date: 2006-07-06
forum: Desktop Environments
---

### Post by DanWan on 2006-07-06
Did anyone manage to run baghira with this system? If yes how?

Terminal always gives me:confused:  an error suggesting the windows manager is already in use and I should replace.

But replace what?

---

### Post by mannheim on 2006-07-06
Do you mean that you are currently using ubuntu (i.e not kubuntu) and you want to use kwin as your window manager?

If so, a first step is to open up a terminal window (or hit Alt-F2 to get the "Run" dialog) and do:

```
kwin --replace
```

Assuming you have installed kwin, this command should replace the currently running window manager (probably metacity) with kwin.

If kwin is already running, you can choose baghira as your kwin theme. Right-click on a title bar and select "Configure Window Behavior".

---

### Post by Snipersnest on 2007-08-01
I'm just wondering.. Does that package come with all the icons and other things?   Or is there an easy way to just enable the whole theme once you pull it from Synaptic?  Thanks

---

