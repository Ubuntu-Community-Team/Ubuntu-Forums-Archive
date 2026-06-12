---
title: "help removing emerald"
date: 2008-04-07
forum: Desktop Effects &amp; Customization
---

### Post by snobby500 on 2008-04-07
Hi i just wanted to know, how can i:

1) remove emerald theme

2) Stop it from starting on startup

3) switch back to metacity

4) I just want to know, what exactly is gtk, so far my understanding is its basically like metacity but changes not only windows but the menu bar and background? Also would this be more stable than emerald - because i lost my window bars once in  a while. also ive been looking for a way to change my menu bar, is this it? Lastly i know you drag and drop themes into the manager, but i know some themes need other engines, would these also just be drag and drop and also are they very stable, or would they cause problems like emerald?

i think thats it

thanks for any help

---

### Post by renzokuken on 2008-04-07
if you want to revert to metacity simply open a terminal and run

```
metacity --replace
```

then to stop emerald loading at start go to System - Prefs - Sessions and in the Startup tab uncheck emerald

---

### Post by andahunter on 2008-04-07
well in ccsm u can do that i think just dont remember how exactly

---

### Post by renzokuken on 2008-04-07
> **snobby500 said:**
> Hi i just wanted to know, how can i:
4) I just want to know, what exactly is gtk, so far my understanding is its basically like metacity but changes not only windows but the menu bar and background? Also would this be more stable than emerald - because i lost my window bars once in  a while. also ive been looking for a way to change my menu bar, is this it? Lastly i know you drag and drop themes into the manager, but i know some themes need other engines, would these also just be drag and drop and also are they very stable, or would they cause problems like emerald?


Think of GTK as the "Controls" in gnome, i.e. the buttons, menus and panels. 

Metacity and Emerald are purely window decorations, i.e. the borders and title bars (minimise, maximise, close etc) of the actual window.

A standard Gnome/Ubuntu install will use GTK controls and the Metacity window decoration. Emerald is simply a replacement for Metacity but GTK controls are still being used while Emerald is running.

Hope that makes sense.

Check out [www.gnome-look.org](www.gnome-look.org) and look at the GTK2 and Metacity sections, you should see the difference in what they control.

---

### Post by snobby500 on 2008-04-07
I tried to look in sscs but i couldnt find it, also i did metacity --replace but, although it worked, i went to appearance>visual effects and put it to normal and then it started up emerald again. 
Also i couldnt find emerald in startup under session,but, could it be:
visual (auto start your preferred AT)

thanks for help so far

---

### Post by snobby500 on 2008-04-07
Thanks, got everything sorted by uninstalling emerald
also, metacity explanation makes it crystal clear, thanks : )
thanks for help

---

