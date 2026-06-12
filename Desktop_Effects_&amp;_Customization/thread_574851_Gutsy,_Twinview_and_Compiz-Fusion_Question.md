---
title: "Gutsy, Twinview and Compiz-Fusion Question"
date: 2007-10-13
forum: Desktop Effects &amp; Customization
---

### Post by jacrider on 2007-10-13
Searched and searched and couldn't find anything about this.

I have a nVidia card (7600 GS) and dual monitors.  I have TwinView working in Gutsy with Compiz-Fusion.

When I first set it up, I had the desktop as one, with the toolbars going across both screens and when the cube rotated, it was rotating as one.

After a recent set of updates, I now have the screen operating as two different cubes, and only tool bars across the left screen, the right having neither of the toolbars.  The desktop still acts as one big desktop, allowing me to drag window from screen to screen.

Any ideas on what I need to get back to one big screen/cube?

Thanks.

---

### Post by amadeus266 on 2007-10-13
In ccsm under desktop cube, change the setting under general-> multi output mode to 'One big cube"

---

### Post by jacrider on 2007-10-18
Amadeus:  Thanks!  I now have one big cube.

Any ideas on how to get my menu bars to span both screens?

Thanks.

---

### Post by Inxsible on 2007-10-18
Are you having any problems in terms of lag on the second monitor ?

I have had that problem in Feisty with TwinView (I have the same card). I am not sure if I should upgrade or perform a fresh install.

---

### Post by evissecx on 2007-10-19
I have the opposite problem. When i configure twinview, i got the panels across both monitors.
But I really want the panels just on my main monitor. Also with this configuration, I can't maximize windows on 1 monitor, it get strecthed over both.

---

### Post by jacrider on 2007-10-19
Inxsible:  I have no problem with screen lag.  I wonder if you monitors have (very) different refresh rates.

evissecx:  I agree that the window maximize when the panel spans both monitors is a pain.  I do like the additional real-estate on the panel however.  I rarely maximize anything.

---

### Post by Vodkaneat on 2007-10-19
I have the same problem as evissecx, its as if twinview is ignoring my metamodes and spanning both monitors

---

### Post by snoe on 2007-10-19
I too have evissecx's problem. It seems compiz doesn't realize there are two screens?

---

### Post by snoe on 2007-10-19
Found a solution. 

Go to compiz settings manager->general options->display settings tab
UNCHECK detect outputs (yes uncheck)
and under outputs put two entries (depending on your resolution) like:
1280x1024+0+0
1280x1024+1280+0

restart X and maximize works (for me at least)

---

### Post by ph8 on 2007-10-20
Brilliant, works (for maximising!)

Any idea how to get the panels to only span the 'main' screen?

---

### Post by hofsmo on 2007-10-20
If you want the panel to spawn on only one screen you can right click it, choose properties and uncheck expand, then you'll get a small panel, which you can move wherever you want. You can also run "gconf-editor", navigate to "/apps/panel/toplevels/top_panel_screen0", then try to change the value for monitor or screen.

---

### Post by raydar on 2007-10-21
Thanks, Snoe--that worked for me too, for making a window maximize on whatever screen it starts out on (instead of across both).

EDIT: Crud. Maximizing works okay now on both monitors, as does View-->Fullscreen on the PRIMARY monitor; but if I go View-->Fullscreen in a (Firefox) window that's on the SECONDARY monitor, I still get a two-monitors-wide "window," which is in full-screen mode in that there are no menus, etc., but it's offset from the actual edges of the screen and can be dragged around & resized with the mouse like a non-maximized window. Interestingly, if I begin with my window on the primary display and do View-->Fullscreen, then drag the full-screen window to the secondary monitor, the window snaps to the right size on the secondary monitor.  Seems it just can't find the right full-screen-mode size if it starts on the secondary monitor.

I second the motion for getting my panels to stretch across just the primary display . . . .

---

### Post by snoe on 2007-10-22
For the panels, I "add to panel" and choose a separator just at the right edge of the first monitor, the right click that separator and "lock to panel" this way, nothing to the left of the separator will expand beyond the first monitor.

Not perfect but good enough for me.

---

### Post by raydar on 2007-10-22
Ha--that's great; I never would've thought of that.  Took me a bit to get the hang of manipulating everything (unlocking, locking, clicking "Move," etc.), but thanks to you both my top & bottom panels look more or less like they ought to.  Thanks!!!  :)

---

### Post by Shootfast on 2007-10-25
I also have the lag when using Compiz-Fusion and Twinview, but only on screen 0, screen 1 is fine. And yeah, the monitors do have different refresh rates. One's a 1680x1050 LCD (lagging) and the other's a 1024x768 CRT.

---

### Post by fearlsgroove on 2008-03-21
To fix the panel spanning both screens, try setting your second screen to relative (rightof, leftof, etc) in nvidia-settings instead of absolute. This fixed the issue for me. Full screen also seems to work fine everywhere.

---

