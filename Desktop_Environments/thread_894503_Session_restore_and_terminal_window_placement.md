---
title: "Session restore and terminal window placement"
date: 2008-08-19
forum: Desktop Environments
---

### Post by csavage on 2008-08-19
I use a lot of terminal windows and like to have a few of them already laid out when I login, so I save their placement using the Session system.  However, when I login, Gnome usually likes to slightly shift them around from their original positions, just enough that I need to move them all back.  The attached figures show how I want them/save the session (second image) and how Gnome usually restores them (first image).  In the second case, some of the terminals are shifted far enough down so that the last line or two is hidden behind the taskbar.  How can I get the the session restore to put the terminal windows exactly where they were saved?

Gnome does not always shift the windows about, I would say about 10-20% of the time the windows are actually placed *correctly*.  So it seems like it can be done, but there is something that is interfering.  I will say that the top windows often seem to be shifted down enough to leave room for a taskbar at the top of the screen (the Gnome default, but which I removed); that may simply be a coincidence.  Any ideas?

I have tried taking different snapshots ("Remember Currently Running Applications") in case the first snapshot was somehow corrupt, but that did not change anything.

Maybe a completely separate issue, but after a session restore the taskbar lists the terminal windows from *all* desktops, even though I have it set to only display applications in the current desktop (you can see six terminals listed in the first figure, even though only three windows are visible).  Going to the correct desktop and clicking on the actual window clears that window from the list on other desktops.  This is only a minor annoyance compared to the above issue, but also seems to be a startup/session restore issue.

---

### Post by kaibob on 2008-08-19
Perhaps an alternative approach would be to use the gnome-terminal --geometry option which allows you to specify the window size and location. Put multiple instances of the gnome-terminal command in a shell script with a separate size and location for each terminal. Then place the shell script in the sessions applet.

A rough example:

> gnome-terminal --hide-menubar --geometry=40x20+0+0
gnome-terminal --hide-menubar --geometry=40x20+0+700
gnome-terminal --hide-menubar --geometry=40x40+450+0

---

### Post by csavage on 2008-08-19
I see the geometry already specified in the sessions file, for example:

> --geometry 100x32+5+24

Opening up a new gnome-terminal with this geometry places the terminal in the upper left corner.  It appears exactly the same if I use "--geometry 100x32+0+0".  If I use "--geometry 100x32+5+25", the window is a single pixel from the top, so it appears the geometry option is ignoring the first 5 and 24 in the x and y directions.  These are about the size of the border and title regions of the window, so maybe that has something to do with it.  It is clear that, when saving a session, terminal windows in the upper left corner are considered to be at +5+24.

Here is something interesting, though.  If I run the script:
> 
gnome-terminal --geometry 100x32+5+24 &
gnome-terminal --geometry 100x32+5+24 &
gnome-terminal --geometry 100x32+5+24 &
gnome-terminal --geometry 100x32+5+24 &
...
All but the first of these terminals seem to randomly appear in either the upper left corner or (5,24) pixels from it.  If I run the script again, I will find different ones that have shifted.  The one on the first line, however, is always in the upper left corner, never shifted.

I don't know if this is a gnome-terminal issue or something with the window manager.  Yes, I could do a script and use +0+0 to put a window in the upper left corner.  But, while I use like to use the same windows, I change the directories all the time, so I find the session manager to be much more convenient (press one button vs. editing a bunch of working directories in the script).  It would be nice if this worked!

---

### Post by kaibob on 2008-08-19
> **csavage said:**
> Opening up a new gnome-terminal with this geometry places the terminal in the upper left corner.  It appears exactly the same if I use "--geometry 100x32+0+0".  If I use "--geometry 100x32+5+25", the window is a single pixel from the top, so it appears the geometry option is ignoring the first 5 and 24 in the x and y directions.  These are about the size of the border and title regions of the window, so maybe that has something to do with it.  It is clear that, when saving a session, terminal windows in the upper left corner are considered to be at +5+24....

Do you have a top panel? I have one that is 32 pixels tall, so the following will appear the same as far as the location of the terminal window on the y axis:

> gnome-terminal --geometry 100x32+0+0 
gnome-terminal --geometry 100x32+0+32 

I do see a small difference (5 pixels in the x axis) between the following:

> gnome-terminal --geometry 100x32+0+0 
gnome-terminal --geometry 100x32+5+0 

---

### Post by csavage on 2008-08-19
> **kaibob said:**
> Do you have a top panel? I have one that is 32 pixels tall, so the following will appear the same as far as the location of the terminal window on the y axis:
No, there is no top panel, only a bottom panel (see the figures I attached in the OP).  If I do "--geometry 100x32+5-Y", I have to increase Y to about 56 before the terminal window begins to move away from the bottom panel, which is 50 pixels wide.  It appears the play I have on each side is 24 (top) and 5 (left, right, bottom) pixels, which seems to match up with the border and title bar sizes.  The issue only seems to arise when I try to open several windows at once or in rapid succession.

I think I have discovered something.  When I turn off the Compiz "Window Decoration" function, the windows all seem to obey the geometry option!  They drawback is that windows then have no borders or title bars (no minimize/maximize/close button at the top).

As far as I can tell, the position of the window is always considered to be where the corner of the *internal* pane is (not including border and title bar).  When I switch "Window Decorations" on/off, those windows are shifted to keep the outer corner in the same position.  That is, if the upper left corner is at +5+24 without a border, the whole pane is shifted down and to the right when the border is added (switch decorations on).  Then it appears the final window placement depends upon whether or not the window is placed before or after the borders are added.  The two cases are:

1) The border is added before placing the window.  The internal pane is then placed at +5+24.  The border and title bar fill out 5 and 24 pixels to the left and top, so the overall window is all the way to the upper left corner.

2) The window is placed before the the border is added.  The plain pane is placed with the upper left corner at +5+24.  When the border is added, everything is shifted by +5+24 so that the outer corner is at +5+24 (but the inner corner is now at +10+48).

So I think what is happening is that, when many windows are opened at once, some borders are not getting drawn before the window manager tries to place them.  Some sort of race between adding the borders and placing the windows.  I think that makes this a bug, but I don't know what I should file a report under (Gnome?  Compiz?)

---

