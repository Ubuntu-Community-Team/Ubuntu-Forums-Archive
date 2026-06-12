---
title: "Screen Resolution Issue"
date: 2009-04-25
forum: General Help
---

### Post by Reynbow on 2009-04-25
Okay so with some annoying fiddling I finally got the Nvidia driver installed.
Everything is all nice and pretty, cool effects etc, nice resolution. 
All is great untill I restart, then my resolution reverts to 800x600 and we're back to ugly Ubuntu... Now understand that I have only been using Ubuntu for 1 day and this is the first time I have ever used it... Everything is scary and confusing xD

Anyway, I figured I must have to save the resolution settings or something, so I went to the Nvidia settings, went to save it and this is what I'm presented with;

[img]http://i40.tinypic.com/2w6asgj.png[/img]

Help please, anyone? =]

---

### Post by regor210 on 2009-04-25
I use sysinfo.

sudo apt-get install sysinfo

then 

sudo sysinfo

then just click on the tabs as needed and save your setting. 

Note. You will be in root so make wise choices.

---

### Post by fatriff on 2009-04-25
Yes, you must be in root to save the config file, I'm surprised this problem crops up so often, I was a 1st time user a week ago and the same thing happened to me, so I switched to root and tried it again and problem solved :)

---

### Post by Reynbow on 2009-04-25
Okay guys, treat my like a child.
I have no idea what all that meant... lol

Root? Sysinfo? What? =\

---

### Post by regor210 on 2009-04-25
goto Application>Accessories>Terminal

and type in

sudo apt-get install sysinfo

then type

sodo sysinfo

---

### Post by Reynbow on 2009-04-25
Thankyou very much guys, helped me a lot =]

---

### Post by fatriff on 2009-04-26
I also notice from your screenshot your setting the display as separate X screens, I think you will have issues with sep X screens from what i've read about it on here. Twinview is the way to go.. 

If you have 2 monitors set to twinview the desktop will span both screens but if you maximize an application on either display it will only take up one of your screens.. so in a sense they appear separate anyway.. Only a couple of games I tried spanned the entire 2 screens, 1 was hedgewars and that was just great for playing that.. think WORMS for windows.

On my Twinview, I have XP on screen B and all the ubuntu stuff on A.. I also have multiple desktops set up as virtical so a whole 2 blank screens appear when I switch desktops down rather than scrolling across.

---

