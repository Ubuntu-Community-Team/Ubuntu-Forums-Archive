---
title: "Emerald + 11.04 - options?"
date: 2011-06-05
forum: Desktop Environments
---

### Post by davidryder on 2011-06-05
It's been a while since I've run Ubuntu as my main desktop and it looks like a lot has changed. I hate Unity (seriously, way too much eye candy and not enough practicality) and so I switch to classic and Emerald doesn't seem to be compatible with it. 

I tried Gnome but it too has changed beyond what I'm comfortable with. 

So how do I get Emerald to work with 11.04? Will KDE work? Is there another option to have the classic look + the customization power I had with Emerald?

---

### Post by Copper Bezel on 2011-06-05
You can get back to the Classic look by logging out and selecting Classic in the session menu below the login box after selecting your name, and there's a recompiled version of Emerald [available here]("http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html"). = )

---

### Post by MoRoBoShi on 2011-06-05
I'm trying to do the same.
Since I've switched from unity to gnome3 (with ubuntu-gnome-remix) the windows loses theri buttons, even if everything appears good in the gconf-editor (:maximize,minimize,close under Desktop>gnome>shell>windows).
This configuration doesn't  work at all with Emerald as windows decorator.
If i use GTK windows decorator i cannot see button (as i said) and clicking on the upper left corner of a window cause it crash and  I need  to reload it via  the fusion-icon>reload window manager button.
I would like to have back the old "change desktop background" or "Apperance preference" menù instead oh the "tweak advanced settings". Another couple of days and maybe I will move back to 10.10...

---

### Post by MoRoBoShi on 2011-06-05
Thank you[COLOR=Black] Copper Bezel it worked!!!
Emerald is  fine now![/COLOR]

---

### Post by Copper Bezel on 2011-06-05
Holy crap, it works with Gnome 3? I didn't know *that*. Sweet. = )

---

### Post by davidryder on 2011-06-05
> **Copper Bezel said:**
> You can get back to the Classic look by logging out and selecting Classic in the session menu below the login box after selecting your name, and there's a recompiled version of Emerald [available here]("http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html"). = )

Thanks.. I found that though. I'm on KDE right now and like it so far but I still can't get Emerald to work. When I tried Gnome classic it wouldn't even load my desktop and I really didn't feel like messing with it. 

And recommendations on KDE customization?

---

### Post by Copper Bezel on 2011-06-05
Well, one problem at a time - What problems are you having with the new Emerald PPA? 

(I'm not really a KDE guy, but it's highly configurable, moreso than Gnome in many ways, and there's always KDE-Look.org.)

---

### Post by davidryder on 2011-06-05
> **Copper Bezel said:**
> Well, one problem at a time - What problems are you having with the new Emerald PPA? 

(I'm not really a KDE guy, but it's highly configurable, moreso than Gnome in many ways, and there's always KDE-Look.org.)

KWin is my default window manager right now. I type emerald --replace and there is no effect but I also get no errors. 

So I open Emerald theme manager and choose a theme and nothing happens but in the terminal it says "Reloading..." without error.

EDIT: I did

```
compiz --replace
```

And it started Emerald and changed to the selected theme. But now how can I change things like context menus?

---

### Post by Copper Bezel on 2011-06-05
You have to switch to Compiz first. compiz --replace, then emerald --replace. Compiz is the only window manager with swappable decorations (a Metacity lookalike, a KWin lookalike, and Emerald.)

---

