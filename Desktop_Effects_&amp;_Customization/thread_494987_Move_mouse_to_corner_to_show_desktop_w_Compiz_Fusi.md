---
title: "Move mouse to corner to show desktop /w Compiz Fusion"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by sebast on 2007-07-07
Hi,

Just wanned to know if there is a way to set Compiz Fusion to show my desktop when I move my mouse to a corner of my choice of the screen.

I had that with Beryl and find it pretty useful

Thanks

---

### Post by Happy_Man on 2007-07-07
Sure. Just install compizconfig-settings and then enable the Show Desktop Plugin. Go into its settings, the Misc. Options tab, Movement Direction, tweak to taste.

---

### Post by sebast on 2007-07-07
> **Happy_Man said:**
> Sure. Just install compizconfig-settings and then enable the Show Desktop Plugin. Go into its settings, the Misc. Options tab, Movement Direction, tweak to taste.

But If I get it right, those options are to define how show desktop is handled when the user clicks on the show desktop button in the pannel. But what I want to do is activate this show desktop command just by going to a corner.

In the compiz fusion settings manager, under general options, there his a sections actions which could to the trick, but I don't know the command to use to show desktop.

---

### Post by Happy_Man on 2007-07-07
> **sebast said:**
> But If I get it right, those options are to define how show desktop is handled when the user clicks on the show desktop button in the pannel. But what I want to do is activate this show desktop command just by going to a corner.

In the compiz fusion settings manager, under general options, there his a sections actions which could to the trick, but I don't know the command to use to show desktop.
Yeah, you're right, my bad. But.... Under the General Options --> Actions tab, under General, there is an option for hide all windows and show desktop. Double-click that, and check the corner(s) that you wish!

---

### Post by sebast on 2007-07-07
> **Happy_Man said:**
> Yeah, you're right, my bad. But.... Under the General Options --> Actions tab, under General, there is an option for hide all windows and show desktop. Double-click that, and check the corner(s) that you wish!

Great! Thanks a lot for this.

---

### Post by manutdfan2850 on 2007-07-18
hello,

i enabled this shortcut. and it was working for a few days. then all of a sudden one day it has stopped working. CTRL ALT D still does the same thing, but going to the screen edge has no action...even though it is enabled in the general options. i have no idea whats wrong.... anyone?

---

### Post by woyzeckswoe on 2007-07-24
hi all,

mine isn't working too! under general options  the corner is enabled (bottom right)

btw window picker works well (bottom left)

---

### Post by MilchFlasche on 2007-07-27
> **woyzeckswoe said:**
> hi all,

mine isn't working too! under general options  the corner is enabled (bottom right)

btw window picker works well (bottom left)

Me either! It seems that all the edge actions in General Options -> Actions tab aren't functioning anymore, since I updated Compiz-Fusion a few hours ago.

---

### Post by MilchFlasche on 2007-08-07
> **MilchFlasche said:**
> 
[QUOTE=woyzeckswoe;3074719]hi all,

mine isn't working too! under general options  the corner is enabled (bottom right)

btw window picker works well (bottom left)
Me either! It seems that all the edge actions in General Options -> Actions tab aren't functioning anymore, since I updated Compiz-Fusion a few hours ago.[/QUOTE]
Just to tell you that I have bumped accidentally to fix this. I changed the keyboard shortcut to the Show Desktop item, from "Ctrl+Alt+D" to something else (mine is "Super+D"), and then suddenly the "hot corner" setting of that item (mine is BottomRight) is working now! Maybe you could try this!:popcorn:

---

### Post by Teneul on 2007-10-04
Still not working for me :( any ideas?

---

### Post by ariel on 2007-10-23
same problem here with 7.10 final. looks like an unfortunate bug. Workaround, anyone??

thxs!

---

### Post by dmber on 2007-10-23
you need to go into Preferences in your ccsm (Advanced Desktop Effects Settings) and make sure you're set to Flat-File Backend.

---

### Post by ariel on 2007-10-23
Found a workaround without changing compiz backend. Using GCONF directly.

Documented in the launchpad bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156421](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156421)

---

### Post by jackmc on 2007-11-18
> **ariel said:**
> Found a workaround without changing compiz backend. Using GCONF directly.

Documented in the launchpad bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156421](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156421)

Thanks a lot, been wanting this for a while :)

---

### Post by schnulzrich on 2007-12-02
i was able to get the "show desktop" hot corner working (thanks for the tip, ariel!), but now i have another problem: windows and panels interfere with hot edge detection. for example my lower right corned is set to "show desktop"-- i have a panel on the bottom of my desktop, and if the panel is set to "expand" (thereby covering the bottom left corner) "show desktop"  doesn't work when i mouse to the bottom right of my screen. if i uncheck "expand", exposing the corner, it works fine (of course, if a window contracts to that corner, i can't *un*show desktop without the panel applet, because the window is now covering the corner).

same thing happens with other hot edges. if there's a window extending off (say) the left edge of the screen, and i try to drag another window to the desktop to the left of my current desktop, edge flip doesn't work. or if there's a window overlapping the top left corner, which i have bound to screen wall, screen wall doesn't trigger. if i move the windows out of the way, everything works fine.

anyone else experienced this / know what's going on? is there a workaround?

many thanks!

---

### Post by brothermalcolm on 2007-12-05
Can you please elaborate on how to do that?

@ Ariel
Also I've tried the workaround you found, it works, but it's not great since you have to reconfigure each time you logoff/restart

---

### Post by brothermalcolm on 2007-12-05
> **dmber said:**
> you need to go into Preferences in your ccsm (Advanced Desktop Effects Settings) and make sure you're set to Flat-File Backend.

Yeah, I was meaning if you could elaborate on this please

---

### Post by brothermalcolm on 2007-12-05
> **dmber said:**
> you need to go into Preferences in your ccsm (Advanced Desktop Effects Settings) and make sure you're set to Flat-File Backend.

OK thanks alot I've set my backend to flat-file and now the showdesktop bottomleft screen edge hotkey works and stays after restart

But it seems like I need to redo all the other plugin settings (such as expo screen edge) again because of this change

---

### Post by MilchFlasche on 2007-12-14
> **brothermalcolm said:**
> OK thanks alot I've set my backend to flat-file and now the showdesktop bottomleft screen edge hotkey works and stays after restart

But it seems like I need to redo all the other plugin settings (such as expo screen edge) again because of this change
Hi, I have tried setting to flat-file end too, and in my experience only a few settings have to be redo (maybe this is because I have used flat-file end long before I switched to GCONF backend, so many of the settings actually were kept in backstage). For people who are afraid of losing their settings, perhaps you could export the profile before switching to flat-file backend, and then re-import the settings.

Actually I found that changing backend to flat-file really solves a lot of problems, including "mousewheel on screen edge to switch viewport" issue and some more.

---

### Post by Afkpuz on 2007-12-27
Switching to flat-file configuration worked for me

---

### Post by dakira on 2008-01-22
Hey,

I finally found a solution to this and found out what the real bug is.

Open CCSM and go to Preferences and uncheck "Integration". This setting is supposed to make compiz use gnomes default settings. If these contradict each other in any way it simply doesn't work. You won't miss it, so just deactivate it ;)

---

### Post by boombox1387 on 2008-02-26
I'm still having some problems with this.  Here's what I've tried:

Unchecking the "Integration" box under Preferences in CompizConfig doesn't seem to do anything for me.  Has anyone else gotten this solution to work?

In gconf-editor I navigated to apps > compiz > general > allscreens > options and added the value TopRight to show_desktop_edge.  This also didn't seem to do anything for me.

Changing the backend to Flat-File Configuration works, but using that backend I can only have 2 workspaces and I'd like to have 4.  Is there a workaround for this?

Anyway, if anyone could help with this, that'd be awesome.

---

### Post by dakira on 2008-02-26
Hey.. if deactivating the "integration" doesn't work for you (it should) you can still just switch the backend from gconf to flat-file. If that doesn't do the trick than your problem is something entirely different.

---

### Post by boombox1387 on 2008-02-26
> **dakira said:**
> if deactivating the "integration" doesn't work for you (it should) you can still just switch the backend from gconf to flat-file.

Changing the backend to flat-file does fix it, but for some reason flat-file doesn't let me have more than two workspaces.  Thanks for the help, though.  Got anything else?

---

### Post by boombox1387 on 2008-02-26
Actually, when you unchecked the integration box, did you have to restart for the changes to take place?  Because I finally got around to restarting my system and it seems to be working correctly now (with integration unchecked).  I think I'm going to stop messing with things and hope that these changes stick.

Thanks again.

---

### Post by dakira on 2008-02-26
Yeah.. i should have mentioned that, sorry. You need to restart!

---

