---
title: "Gnome Panel Website Launchers Fail on Reboot"
date: 2008-12-05
forum: Desktop Environments
---

### Post by coldstatue on 2008-12-05
Hey all. I'm running Hardy, but this has been going on at least since Feisty. If I drag the favicon from my Firefox address bar to a Gnome panel, I have a launcher that will open that webpage.

But if i change the icon to anything but the default (I've tried various formats), logouts/reboots cause the launcher to lose all of its data; I get the default launcher icon, and the URl is lost. 

I used to have this problem with panel app launchers too, until I began creating them in their own directory, then dragging to the panel. This doesn't work with weblinks though. 

It's happened with all kinds of sites, but right now, 3 Google Docs are the problem. Like I said, if I leave them on the top panel, and don't change the icon, they are fine. (I've tried moving my customized icons to /usr/share/icons)

TIA

EDIT: I posted this in the wrong category, didn't I? Sorry about that.

---

### Post by kaibob on 2008-12-06
I had a similar problem, and the solution was to preface the URL with firefox, as in the following:

```
firefox http://www.weather.com/
```

I never had an issue with application launchers failing to work, so our situations might be different. Still, it's worth a try. 

As an aside, I've reported this thread to the mod's to see if it should be moved to another forum.

---

### Post by coldstatue on 2008-12-06
Thanks for messaging the mod. Didn't mean to be lazy, I just didn't think to look for the forum's mod... 

I tried the firefox prefix, but it didn't work.

I think it may be happening only with links to Google docs now....
but it works if I leave the icon alone! Doesn't matter what format I choose, or who can access it, or where it's located, etc. 

The old launcher problems were fixed when I started creating them in their own folder in my ~/. 

Initially, I would create them on the desktop and drag them to a panel. Since they didn't exist anywhere else, the panel lost all the info that existed in some temp space, I guess.

I've had this problem in various forms on different computers since Dapper, I think. I've gotten used to seeing the default, data-empty launcher icon on my panels. 

It may be silly, but the default URl icon with my iconset looks really horrible when duplicated 10 times in a row. :p

---

