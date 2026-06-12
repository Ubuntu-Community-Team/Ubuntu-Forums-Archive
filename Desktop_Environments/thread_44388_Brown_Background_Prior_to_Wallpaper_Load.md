---
title: "Brown Background Prior to Wallpaper Load"
date: 2005-06-25
forum: Desktop Environments
---

### Post by GML3G0 on 2005-06-25
Hey. Just got ubuntu up and running and everything set up and all i can say is wow. 

Went from Mandrake 10.0 > SuSE 9.1 Personal > Fedora Core 2 > Slackware 10 > Mandrake 10.1 > Fedora Core 3 > Slackware 10.1 > Fedora Core 4 > Ubuntu 5.04.

Ubuntu has been the best so far. Slackware wasn't bad, just couldn't get my network adapter to work with it.

One gripe with it though. I changed all the GDM and gnome splash screen themes, but the brown background is still there before my wallpaper loads. How do I change that. Thanks.

---

### Post by mattack on 2005-06-25
System -> Preferences -> Desktop Background
or right-click on the Desktop and click on Change Desktop Background

near the bottom of the windo that pops up is something called Desktop Colors. You can select the color there and if you want a gradient or solid color.

---

### Post by scoon on 2005-06-25
[QUOTE=mattack]System -> Preferences -> Desktop Background
or right-click on the Desktop and click on Change Desktop Background

near the bottom of the windo that pops up is something called Desktop Colors. You can select the color there and if you want a gradient or solid color.[/QUOTE]

Hey there, 

Actually, that color gets set in gdm.conf.  Open up that file and do a search for BackgroundColor.

regards, 

scoon

---

### Post by byen on 2005-06-25
[QUOTE=mattack]System -> Preferences -> Desktop Background
or right-click on the Desktop and click on Change Desktop Background

near the bottom of the windo that pops up is something called Desktop Colors. You can select the color there and if you want a gradient or solid color.[/QUOTE]
 nope. mattack nailed it. that is the way to go!  used it myself.

---

### Post by GML3G0 on 2005-06-25
Great! Thanks a lot.

---

### Post by autocrosser on 2005-07-09
Thank you Scoon---
That is what I was looking for---wanted to just have a black background while everything was loading--I had a problem with the brown-just didn't go with where the rest of my prefs were---

Cheers!!
Dean :)

---

### Post by ana_nan on 2007-03-23
> **scoon said:**
> Hey there, 

Actually, that color gets set in gdm.conf.  Open up that file and do a search for BackgroundColor.

regards, 

scoon

Anyone there?

Actually neither methods worked for me.  The color I get is different than the one specified via Desktop Color in "System -> Preferences -> Desktop Background" AND different than the BackgroundColor defined in "gdm.conf".

I have Beryl and cario-dock installed. Is it because of any of these?

---

### Post by scoon on 2007-03-23
Hey there, 

I don't know as I don't use either of those.

-scoon

---

### Post by fracturedmorals on 2008-03-07
> **ana_nan said:**
> Anyone there?

Actually neither methods worked for me.  The color I get is different than the one specified via Desktop Color in "System -> Preferences -> Desktop Background" AND different than the BackgroundColor defined in "gdm.conf".

I have Beryl and cario-dock installed. Is it because of any of these?

Same problem here.......thinking of going as far as doing a grep for the hex color code in /etc.

I'll post if I find any results......

---

### Post by fracturedmorals on 2008-03-07
FOUND IT

It's a dirty fix, but it works.

```
sudo gedit /etc/gdm/PreSession/Default
```

Search for DAB082 (That's the hex code for the default brown...I changed it to 000000 for black.)

:)

---

### Post by Nythain on 2008-03-07
yeah, there's actually a small chunk there (i cant remember teh exact block) that you can coment out that will allow you to actually set teh color the way you are supposed to, in the splash screen or gdm editor... i can have more info once i get home, win98 at work :(

EDIT: Ok, so you dotn comment it out, but you can change the color code to x instead, as discussed in this thread
[http://ubuntuforums.org/showthread.php?t=597282](http://ubuntuforums.org/showthread.php?t=597282)

---

