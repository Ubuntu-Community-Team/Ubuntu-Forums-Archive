---
title: "Script for placing windows on multiple monitors"
date: 2009-11-29
forum: Desktop Environments
---

### Post by wd5gnr on 2009-11-29
I had a monitor fail yesterday so with the big sales going on I bought a new widescreen monitor. I liked it so well I bought another one just like it to replace the monitor that did not fail. So I went from 2 1280x1024s to 2 1600x900s. The 3200 pixel resolution screams for some way to divide the screen up reasonably. Yes I know about tiling window managers, but I just want some things tiled some time.

So... I wrote a script. It works best if you assign it to a global shortcut.  Here's the comments from the script:

```
# Dual Monitor Window placement script -- Williams alw@al-williams.com
# Version Beta 1, November 28 2009 - http://www.hotsolder.com

## This little script chops your screen up into 8 zones:
#  ABCD
#  EFGH
# (Obviously I'm assuming you have two monitors horizontally)
# So your left screen is ABEF and your right screen is CDGH
# You can also use 1 for the left screen and 2 for the right screen
#
# How to use it: Run this script (hint: assign it a global shortcut key)
# It will prompt you to press OK and then click on a window
# Then it will prompt you to enter the grid letters. Enter them in order.
# So you might enter A to get it at the top left or GH to get a double
# wide window at the bottom right. Or DH to get a double high window. 
# if you enter CDGH or 2 the app will jump to the 2nd screen
#
# What you need: 
# Stuff you can get out of the repos:
# Bash (duh), zenity, xwininfo, gawk, wmctrl
# You also need to use a window manager that works with wmctrl (most do)
#
# The script picks up the reported size of your screens automatically 
# This could be a problem if you have two mismatched screens since
#  know at least TwinView (NVidia) reports a bigger size (so if your
#  screens are 1600x900 and 1600x1024, TwinView reports 3200x1024
# So you may want to override
# Also, you will want to trim down the exact values so the window edges
# and all fit. You can adjust WTRIM and HTRIM below or use the options

# Options (all optional)
# -w 10 - Set width trim to 10
# -t 40 - Set height trim to 40
# -i 0x4942 - Use window ID instead of prompting for window
# -n 'mywin' - Identify window by title instead of prompting 
# Note: -n doesn't work well when 2 windows have same title!
# Note: Use -i -n or nothing but do not use -i and -n together
# -x 1600 - Override screen width to 1600
# -y 900 - Override screen height to 900
# -s ABEF - Use placer string and don't prompt
# -r - Do not raise window
# -q - Quiet (do not show intro dialog)

# TODO: Custom grid dialog to pick on a 4x2 grid
# I may do this with kdialog and/or pick zenity or kdialog depending on
# which is available
```

So if your monitors are stacked vertical or any of a host of other differences this may not work for you but maybe you can adapt it. I would like to do something nicer for the position dialog. But that's version 2. I can't decide if I want to do a dialog with like check boxes or buttons that stay pushed or if I want to just capture the mouse and let you draw roughly where you want it and figure it out from there.

I've attached the script to this note as a text file. If you extract it, you'll need to make it executable and will want to change the name (e.g.:
```
mv place-beta1.txt place
chmod +x place

```)

Of course, it ought to be on your path unless you specify a full path in your shortcut. I have a ~/bin directory on my path for just such things. 

Comments welcome. Patches even more so. I use KDE but since I get the sense that is the minority I used zenity instead of Kdialog (see comments for all the dependencies).

---

### Post by wd5gnr on 2009-11-29
Oh, and if you know of anything else that provides multimonitor features I'd be interested to hear about it.

On Windows there are several programs that do things like add a title bar button to send a program to the other screen etc. That'd be cool.

---

