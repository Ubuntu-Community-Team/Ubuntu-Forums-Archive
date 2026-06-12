---
title: "Panel moves to top and won't go back to bottom"
date: 2009-01-29
forum: Desktop Environments
---

### Post by jamesisin on 2009-01-29
I have a panel at the bottom set to not expand, and every time I reboot my system it moves to the top--right over the expanded panel that lives there.

I cannot merely change its panel placement to "Bottom" as it automatically switches the dropdown back to "Top" right before my eyes.  Changing it to "Left" (or "Right") produces equally odd behaviour (see screen shots).

In order to move the panel back to the bottom I have to first turn Expand ON.  Then I am able to move the panel to the bottom (and I can then turn Expand back OFF).

This looks like a bug, but can anyone confirm this behaviour?  Is there already a bug reported?


====================


Top:

[IMG]http://www.soundunreason.com/SlopBucket/PanelTop.png[/IMG]

Left:

[IMG]http://www.soundunreason.com/SlopBucket/PanelLeft.png[/IMG]

---

### Post by RottenBananas on 2009-01-29
Hey pal, I had the same problem. The guy that replied had the solution. Heres the thread

[http://ubuntuforums.org/showthread.php?t=697718](http://ubuntuforums.org/showthread.php?t=697718)

---

### Post by jamesisin on 2009-01-29
Ok, so this I think will be helpful.  I'll have to log out/in to get the fuller picture (ie: to see if it throws my panel wherever).

Basically, if I run **gconf-editor** (through a terminal) and navigate to **/apps/panel/toplevels/** I find four panel entries (four?).  Through a little experimentation I was able to figure out which entry was for my bottom panel (here called Panel_3).

I did find one very useful item:

disable_movement

With this checked I was not able to move a panel.  Now I know what to do if I encounter that problem (hopefully).

I'm not sure how to read the coordinate information in the editor though.  I have the following settings showing:

x = 420
x_centered = [x]
x_right = 0
y = -18
y_bottom = -1
y_centered = [_]

What might I need to change in this to ensure that this panel prefers the bottom?  (orientation above is already showing bottom.)

---

### Post by jamesisin on 2009-01-29
Well, that doesn't really appear to have helped any.

On reboot my panel was once again at the top.  If I uncheck disable_movement and even manually type in "bottom" it magically changes it back to "top" (f^c#!ng annoying).

My coordinates read as follows:

x = 413
x_centered = [_]
x_right = -1
y = -27
y_bottom = -1
y_centered = [_]

As per before, having it expand allows me move it to the bottom.  Then I can turn expanding off and it stays there (presumabley until I reboot/logout).

Really at a loss here.

Any ideas?

---

### Post by RottenBananas on 2009-02-02
I got nothin then... I keep mine at the top unexpanded. My resolution is 1280 by 800. I have y_bottom and y set to 800 and it always shows up where its supposed to up top. So i'd assume both of them set to 0 should stick yours at the bottom. Hopefully someone else can help...

---

### Post by jamesisin on 2009-02-02
RB - Thanks.  Can you try positioning yours at the bottom (unexpanded) and reboot.  See if it moves.  If this effects your system, I ought to report it as a bug.  If yours stays put (at the bottom) then there is something going on with my system specifically.

---

### Post by RottenBananas on 2009-02-10
Hey pal, sorry haven't checked the forums in awhile. I tried what you said and when I restart, it hops up top for a second and then moves down to where its supposed to be a couple seconds later. A little odd but it does end up where its supposed to be

---

### Post by jamesisin on 2009-02-10
Well, thanks for testing it.

I suppose that's important information and maybe someone else will stop in and provide another piece of the puzzle.

I don't understand it one bit.

---

### Post by jamesisin on 2009-03-31
So, still no solution.  I have this clumsy work-around whereby I can move the panel back to the bottom everytime I log back in, but that's lame.

I can say that the panel I am using is not the original bottom panel.  Is it possible to re-create the original bottom panel (perhaps by copying and pasting the segment of code for that panel) in this machine (from another machine or profile)?

This way I could test if the problem was any panel or merely newly created panels (the panel I created is not called `bottom_panel_screen0` but is instead called `panel_3`--and there seems no way to change that).

---

### Post by UbuntuNerd on 2009-03-31
try this code in a terminal to restore your panels to default and then see if it works:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```
also there is an option to lock down your panels

---

### Post by jamesisin on 2009-04-01
Well, you have brought me to the files I need to emulate/remodel so that's good enough.  I am going to pull the xml file from another machine or profile and work out what's different, recreate a `bottom_panel_screen0` folder/panel &c.  I'll report back with my findings.

(And, why the hell is the background neon pink here at the forums?  Is everyone seeing this?)

---

### Post by jamesisin on 2009-04-01
Ok, so that was an adventure.

I realized pretty early on that the number of files I would have to edit wasn't going to be worth the effort.  So I followed your instructions.

Your instructions worked about 99%.  There is just one residual issue.  It was doing this before, but I don't think I bothered to mention it.  The icons in the panel I use for launching sometimes change positions at login.  I have to then unlock them and move them back into position.

Any further suggestions?

(We have moved from neon pink to neon green.  What's up?)

---

### Post by kyle_white on 2009-09-27
This may be a little late, but for anyone who's still running into this problem, try setting apps/panel/toplevels/<paneltofix>/y_bottom to 0 instead of -1. It worked for me :)

---

### Post by theZoid on 2009-09-27
> **kyle_white said:**
> This may be a little late, but for anyone who's still running into this problem, try setting apps/panel/toplevels/<paneltofix>/y_bottom to 0 instead of -1. It worked for me :)

That fixed it for me too...it was set with -1 to be at top like the other panel's settings.  ...now the icons moving to the left...let me check that one...:)

---

### Post by jamesisin on 2009-09-27
kyle_white - As mentioned, I ended up completely rebuilding my panels--or at the very least the problematic ones (for more information see previous posts).  But it is good to see that others are still benefiting from my thread.  Thanks for chiming in.

---

### Post by vtel57 on 2009-11-20
> **kyle_white said:**
> This may be a little late, but for anyone who's still running into this problem, try setting apps/panel/toplevels/<paneltofix>/y_bottom to 0 instead of -1. It worked for me :)

Man! I have been fighting with this issue for a couple days in my new Debian 5.0.3 AMD64 installation. THIS was the fix I needed! Thanks a bazillion, Kyle! :)

~Eric

---

### Post by zaivala on 2009-12-06
> **jamesisin said:**
> Ok, so this I think will be helpful.  I'll have to log out/in to get the fuller picture (ie: to see if it throws my panel wherever).

Basically, if I run **gconf-editor** (through a terminal) and navigate to **/apps/panel/toplevels/** I find four panel entries (four?).  Through a little experimentation I was able to figure out which entry was for my bottom panel (here called Panel_3).

OK.  I'm just trying to move my top panel to the bottom.  I've searched everything I can think of and come up empty.  I've gone through everything I can think of in System.  It SHOULD be under Appearance, but it's not.

Running Ubuntu Netbook Remix 9.10 KK on an ASUS Eee PC 901.  Should be easy, yes?   I tried typing gconf-editor in Terminal, and got "unknown id: gconf-editor".

Help?  I've done this before in earlier editions of Ubuntu on desktop machines...

---

### Post by jamesisin on 2009-12-06
zaivala - Check Synaptic to see that you have the editor already installed.  It should appear under Applications --> System Tools --> Configuration Editor.

---

### Post by pr0tman on 2010-10-19
As I prefer to use awn vertically on the left, my intention is to have the main gnome panel configured as:

auto-hide
not expanded
bottom

This is because I still like to be able to use alt+f2 "run" and some of the gnome panel features when I want them.

If I am in gconf-editor and set:

/apps/panel/toplevels/top_panel_screen0/orientation

to "bottom"

and uncheck: /apps/panel/toplevels/top_panel_screen0/expand

as soon as I drag over the panel, the orientation value changes back to "top" right before my eyes.

Also, every time I log-in, it will move the panel back to the top; however this is only if left not expanded.

---

