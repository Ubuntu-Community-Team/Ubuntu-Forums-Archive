---
title: "Wine - Apps in full screen"
date: 2007-04-27
forum: Gaming &amp; Leisure
---

### Post by Hawk__0 on 2007-04-27
Hi im trying to play games, some, like starcraft, the top and bottom menu bar things still show when it goes "full screen"

any idea as to how i can make my game a layer above the menu bars?

---

### Post by bluewagon on 2007-04-27
i'd like to know as well..

---

### Post by Hawk__0 on 2007-04-28
bump

---

### Post by cogadh on 2007-04-28
See this post:
[http://ubuntuforums.org/showthread.php?t=423167](http://ubuntuforums.org/showthread.php?t=423167)

---

### Post by Hawk__0 on 2007-04-28
that post did not help.
i mean the 2 horizontal bars on the top and bottom.
they overlap my "full screen" games when emulated thru wine

---

### Post by joebanana on 2007-04-28
I had the same problem till today. I updated wine and turned off desktop effects, but I am too lazy to tell you what actually worked(I think it was wine). hf gl
P.S. new version 0.9.36

---

### Post by DezSP on 2007-04-28
I'd vouch for the wine update.

---

### Post by cogadh on 2007-04-28
> **Hawk__0 said:**
> that post did not help.
i mean the 2 horizontal bars on the top and bottom.
they overlap my "full screen" games when emulated thru wine

While the Wine update may have helped, the sixth post on that page has instructions on how to run a game without your window manager at all, meaning there never are any panels running to get in the way. Using that instruction can also be a significant performance improvement.

Unfortunately for me, the Wine update broke my games so that I can only run games in 800x600 now, no matter what method I choose.

---

### Post by Hawk__0 on 2007-04-28
I have the newest wine, i just checked.  (also, one time wine crashed, then the 3 shortcuts in the applications - accessories menu disappeared... how do you fix that?)and that script broke my linux lol.  well not really.  it just went to a gray 8 bit looking screen with an x for a cursor lol.  i hit ctrl alt f1, then i dont know the command to get back into gui... its "startx" on slackware =\.

but ya the menu is really annoying me too... i had the demo for "crossover" and i didnt liek it so i uninstalled it and got an error then it gave me the command to uninstall from the cmd line, and it doesnt work.. i jsut want to remove it manually.  some stuff is on my root drive then its in my applications menu

---

### Post by Hawk__0 on 2007-04-29
bump

---

### Post by cogadh on 2007-04-30
> **Hawk__0 said:**
> ...and that script broke my linux lol.  well not really.  it just went to a gray 8 bit looking screen with an x for a cursor lol.  i hit ctrl alt f1, then i dont know the command to get back into gui... its "startx" on slackware =\.

That gray screen was a plain X session without a window manager, it's what X looks like underneath Gnome or KDE. Think of it like peeling back the layers of an onion. On the outside is your window manager (Gnome, KDE, etc.), the next layer down is the X server and underneath that is the terminal/console. What that script does is remove the outer layer and allow your game, through Wine, to communicate directly with the X server on a separate terminal from your normal desktop.

If your game didn't launch after that gray screen appeared, then you need to hit CTRL-ALT-BACKSPACE to kill that X session and get back to your normal desktop. CTRL-ALT-F1 just gets you down one layer to the console that was running underneath that plain X session on terminal 3, while your normal desktop runs on terminal 1.

The "startx" command is standard across all distributions of Linux that use a window manager. It didn't work for you because you were trying to startx on a terminal that did not have a window manager set up to run.

It should be noted that the script assumes that you already have the game functional through Wine. If you are not able to get a game to run normally by running "wine /path/to/executable" on your desktop, then using the script won't work either.

Wish I could offer some advice for your Crossover issue, but I've never used it, so I don't want to tell you to "try this" and have it screw things up more.

---

### Post by Hawk__0 on 2007-05-05
SOLVED

I figured out the problem, it involves:
-your version of wine
-desktop effects/beryl

its actually an easy fix, first you need the latest version of wine, then just simply turn off ubuntus build in desktop effects or beryl.  i just right click beryl, go to select window manager, and then click on metacity (gnome default)

---

