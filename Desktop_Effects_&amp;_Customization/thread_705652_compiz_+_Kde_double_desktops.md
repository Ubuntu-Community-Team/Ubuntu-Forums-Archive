---
title: "compiz + Kde double desktops"
date: 2008-02-23
forum: Desktop Effects &amp; Customization
---

### Post by @tticus on 2008-02-23
hey,

   I have just switched from gnome to kde. Though I have set only one desktop in kde when I start compiz it always doubles the screen numbers and the "cube" always has only two sides, no matter how many desktops I set. 
Do you have any clue how can i fix this ? 

Thanks in advance,
    @tticus

I have ubuntu gutsy 7.10 with compiz

---

### Post by rohedin on 2008-02-24
Yep I'm having the problem too. I've tried having different numbers of desktops but no avail :(

Does anybody have an idea as to what's going on? Having a 3D Compiz rectangle just isn't as fun as a 3D Compiz cube..

---

### Post by Weazl on 2008-03-07
I have the same problem. Killing the adept_notifier as suggested elsewhere does not help. Anyone have a solution for this? I'm running an AMD (ATi) card. ^they^ probably have AMD cards as well..

Edit:
When I have 1 desktop configured and hover my mouse over them, the tooltip says "Desktop 1" @ both visible desktops. When I set 4 desktops, the first 4 tooltips correspond to the number of the desktop. Desktop 5-8 all say "Desktop 1", and clicking either one of them flips the 2 desktops a couple of times (the higher the desktop number, the more flips). I don't know, I thought this might be useful to someone who understands what is going on...

---

### Post by SrEstroncio on 2008-03-11
I am having the exact same problem, as you guys and I am running a compaq v4000 with an interl videocard, any ideas anyone?
Thanks in advance

---

### Post by Zorael on 2008-03-12
Compiz and KDE don't play well together out of the box. There's been considerably less effort to integrate it when compared to Gnome. But I'm not in a position to complain, I guess. :>

First of all, add **--ignore-desktop-hints** as an argument when you start compiz. This will make it ignore how many KDE workspaces you've set it up to have and just listen to compiz's settings. **Do note** that your pager applet in your Kicker tray will remain useless, so you're better off just removing it. I use the Expo plugin exclusively, having bound it to activate when I click the top-left corner. Easy enough.

Example:
```
$ compiz --replace --ignore-desktop-hints ccp
```
To my knowledge, adding the **ccp** argument makes it use its own format for storing configuration, which seems to be a good idea to me.

If you're using an Nvidia card, here's my startup script with all my Nvidia tweaks:
```
zorael@azrael:~$ cat /usr/bin/compiz.start
#!/bin/bash

# kill adept_notifier since it bugs out
killall adept_notifier

# invoke compiz with [COLOR="DeepSkyBlue"]KDE[/COLOR] and [COLOR="Lime"]Nvidia[/COLOR] tweaks. [COLOR="DarkOrchid"]pass arguments to compiz[/COLOR] and [COLOR="DarkOrange"]leave terminal control to the user[/COLOR]
[COLOR="Lime"]__GL_YIELD="NOTHING"[/COLOR] compiz [COLOR="Lime"]--loose-binding[/COLOR] [COLOR="DeepSkyBlue"]--ignore-desktop-hints[/COLOR] ccp [COLOR="DarkOrchid"]$@[/COLOR] [COLOR="DarkOrange"]&[/COLOR]
```


Second, leave **Desktops** at 1! It's **Horizontal Virtual Size** you want to set to 4 to get a cube. Or 3 to get a triangle, etc.

---

### Post by SrEstroncio on 2008-03-15
Thanks man, it worked ^-^, just having some minor problems there.

---

### Post by Nythain on 2008-03-15
ok, this really isnt a problem with kde and compiz not playing nice together... as far as i've ever experienced, they've played fine...

as already stated, this is a problem with the fact that compize doesnt use "desktops" for its cube sides... it uses "viewports"... consider them clones of your desktop... the same problem used to show up on these forums concerning gnome too, before compiz was integrated into ubuntu with gutsy...

also... there is a compiz kicker and compiz pager applets available in the repos, or from kde-look that will function better with compiz running than the default kicker/pager

---

### Post by Zorael on 2008-03-15
Er, yes, there's the full explanation.

As for "doesn't play nice together"; when I first wanted a cube, before finding out about this extra --ignore-desktop-hints argument, I ended up with 16x16 desktops. Turns out it was because I had KDE set up to have 4 viewports, and Compiz to have 4 horizontal virtual desktops, since I don't run Compiz at all times - but I do like to use 4 virtual desktops at all times.

That goes for the pager as well; it isn't compiz-aware, so it's useless unless you replace it.

Might be chalked off to semantics, I guess.

---

