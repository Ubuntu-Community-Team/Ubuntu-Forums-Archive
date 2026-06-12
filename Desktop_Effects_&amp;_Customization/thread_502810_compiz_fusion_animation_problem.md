---
title: "compiz fusion animation problem"
date: 2007-07-17
forum: Desktop Effects &amp; Customization
---

### Post by edwin.e.johnson on 2007-07-17
this is my prob....  i just did a fresh feisty install and put compiz fusion on my machine...
everything works well except that the animations wont let me set the duration time.... i try to set it to random and .5000 for the duration but it automatically resets to .0000

anyone else had this prob..?

it worked before i reinstalled the os.  also the menu has changed for selecting the animations it went from a graphic drop down menu to a text menu.

---

### Post by BOBSONATOR on 2007-07-17
Im having the same problem aswell.

---

### Post by edwin.e.johnson on 2007-07-18
anyone else?


none of the 3 updates i have got in the last 3 days have fixed this

---

### Post by SkiesOfAzel on 2007-07-18
Try selecting Flat-flie Configuration Backend and starting compiz with
```
compiz --replace --loose-binding -c emerald &
```

---

### Post by edwin.e.johnson on 2007-07-19
thats a nogo....


is this the way the selection menus are supposed to look now?

text based not drop down?

---

### Post by pressed on 2007-12-07
i've got a similar problem in gutsy, only mine is that i simply can't change turn on animations. other plugins work fine, but not this one. i'm getting wobbly windows but even the default animation for opening/closing windows is gone now [even when i disable 'extra plugins']

i installed compiz-fusion-extras and tried reinstalling, didnt help. if i try to change ~/.config/compiz/compizconfig/Default.ini, my changes get overwritten. if i try to change the animation settings through ccsm, my changes get overwritten. if i try to do a manual plugin sort through preferences, the same thing.

this only happens with certain plugins:
animation, negative, window previews. these are all plugins that were working before. the problem started when i switched on animation with random each time (just to see which ones i liked..) and then restarted.

i'm going to try moving my .config/compiz folder, but it seems to be like some instance of the program is comandeering my settings file. only i don't know how to fix that. anyone got any advice? the suggestion from SkiesOfAzel froze my windows. (for anyone new enough not to know, press CTRL+ALT+BKSPACE if this happens)

EDIT: I removed the entirety of compiz instead of just reinstalling "compiz-fusion-extras" and then reinstalled. works fine now. Also, I took forlong's [advice]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") and made a new profile before changing anything this time... then future problems should be more fixable.

---

### Post by Shockwav on 2008-04-22
Sorry to add to an old thread, but...

ATI x1600 + Compiz has been a no go for me from day 1 due to a long list of issues that aren't relevant. Last week I decided to try again and what do you know!

Sadly, I noticed that the animations aren't working. I tried to resort the plugins and reinstall - no change.

I'm not 100% fixed, but I did hit on something that has got it working.

Compiz Settings Manager
->Animations
-->Effect Settings tab

and select "Random Animations For All Events"
And at least for me it's working.

---

### Post by Arlanthir on 2008-04-25
Custom animations don't work here too :S They're enabled but just don't do anything in Custom Effects mode.

EDIT: Solved by creating a new profile and customizing them again ;)

---

### Post by MickS on 2008-04-26
> **Arlanthir said:**
> Custom animations don't work here too :S They're enable but just don't do anything in Custom Effects mode.

EDIT: Solved by creating a new profile and customizing them again ;)

Solved it for me too.

Mick

---

