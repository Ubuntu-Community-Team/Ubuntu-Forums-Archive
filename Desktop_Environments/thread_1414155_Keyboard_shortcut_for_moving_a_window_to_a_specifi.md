---
title: "Keyboard shortcut for moving a window to a specific display"
date: 2010-02-23
forum: Desktop Environments
---

### Post by wayfarer_boy on 2010-02-23
I noticed that while Compiz has every keyboard shortcut imaginable for moving windows between desktops, there's no shortcut for moving a window to a specific display when using dual monitors.  I thought I'd publish my own solution to this problem here.

So far, I've found the best method is to use the command line automation tool: xdotool - [http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/xdotool.1.html)

Here's what I did:
[list=1]
[*]Test out the xdotool in a new terminal window using this command ```
xdotool windowmove `xdotool getwindowfocus` 100 100
```  This should move your terminal window 100 pixels in from the top left of the leftmost display.
[*]Find out the top-left coordinates of your rightmost display by using the Nvidia X Server Settings tool in Main menu > Administration or via the terminal: ```
nvidia-settings
```
[*]Go to X Server Display Configuration and click the rightmost Display in the layout section.  Its position offset should be displayed in the position field.  Make a note of these two numbers.
[*]Create a script to move your window, either to the leftmost screen or the rightmost screen, using this code or similar:
**move-window-to-display.sh**```
#!/bin/bash

if [ $1 -eq 2 ]
then
    POS="1680 95"
else
    POS="0 0"
fi

/usr/bin/xdotool windowmove `/usr/bin/xdotool getwindowfocus` $POS

exit 0
``` Remember to change the $POS variable to the offset position of your rightmost display.  The script accepts a single argument - either "1" or "2" - to denote the display on the left or right.
[*]Once you've saved the script, make it executable by typing ```
sudo chmod +x /home/username/scripts/move-window-to-display.sh
```
[*]Open the keyboard shortcuts preferences: Main menu > Preferences > Keyboard shortcuts, and add a new custom keyboard shortcut (using the add button at the bottom of the window).
[*]Call it "Move window to display 1", and enter the path to your script, eg. ```
/home/username/scripts/move-window-to-display.sh 1
```  Remember, the number at the end is an argument that denotes the display (1 for left, 2 for right).
[*]Assign a keyboard shortcut to your custom shortcut.
[*]Repeat for the right display.
[/list]
Now when you press the keyboard shortcut, the active window should be moved to either the left or right display!  Hope this helps someone.

---

### Post by offrampextreme on 2010-02-24
Thanks. I haven't tried this yet, but i sure will. I really like speeding up my workflow by using hotkeys and i usually have quite some windows open on two monitors and two desktops, so this will be quite useful.

---

### Post by gfi on 2010-03-10
Thanks for the idea!
I have mapped this to 'Windows Key + Right (or left) Arrow' and can move windows between monitors... 
Would like to extend the script, if I can determine the window position in the first monitor BEFORE the move and manipulate the final position in the second monitor.

Eg, right now, a move will always result in the window going to 0,0 of the second monitor... but if I can determine the window position prior to move, I can move the window to the second monitor, keeping the same 'y' value (x changes, of course).. 

Went thro the functions available in xdotool, but looks like I cannot figure out a way to GET window pos before move. :(

---

### Post by wayfarer_boy on 2010-03-12
After a bit of digging here:

[http://ubuntuforums.org/showthread.php?t=760651](http://ubuntuforums.org/showthread.php?t=760651)

and here:

[http://www.ruby-forum.com/topic/165740#728314](http://www.ruby-forum.com/topic/165740#728314)

it looks like there's a solution.  Try this in your script to get the current active window's X pos (or Y pos, just change the "Absolute upper-left **X**" to "**Y**"):
```
x=$(xwininfo -id `xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)"| cut -d ' ' -f 5` | grep "Absolute upper-left X" | cut -d ' ' -f 7)
```

I've also grabbed the display resolutions via xorg.conf, so here's a new script that implements these changes:
```
#!/bin/bash

offx=$( grep metamodes /etc/X11/xorg.conf | cut -d '+' -f 4 | sed 's/[^0-9]*//g' )
offy=$( grep metamodes /etc/X11/xorg.conf | cut -d '+' -f 5 | sed 's/[^0-9]*//g' )
curx=$(xwininfo -id `xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)"| cut -d ' ' -f 5` | grep "Absolute upper-left X" | cut -d ' ' -f 7)
cury=$(xwininfo -id `xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)"| cut -d ' ' -f 5` | grep "Absolute upper-left Y" | cut -d ' ' -f 7)

if [ $curx -ge $offx ]
then
    newx=$((curx-offx))
    newy=$((cury-offy))
else
    newx=$((curx+offx))
    newy=$((cury+offy))
fi

/usr/bin/xdotool windowmove `/usr/bin/xdotool getwindowfocus` $newx $newy

exit 0
```
There's probably a better sed command to find the display resolutions (I'm definitely no sed guru - in fact, it's a tool I still find incredibly hard to use after years of wrangling with it) and when I use the script to move a window, repeated moves means the window slowly gets lower on each screen, so there's pixels being added to the newy value for some reason, but I can't work out why.

Anyway, let me know if this works for you.

---

### Post by wayfarer_boy on 2010-03-12
Also realised that this script works for horizontal layouts, but if your monitors are place vertically next to each other, you'll need to edit the script so it checks for [ $cury -ge $offy ].  I'm sure there's a simple if statement that can work out if your display layout is horizontal or vertical, but I'm needing to get on with some work!

---

### Post by scallopedllama on 2010-03-17
For our friends on KDE 4: this is supported out of the box.

Open up System Settings > Keyboard and Mouse > Global Keyboard Shortcuts 

In there, pick the KDE Component KWin and the shortcuts in question are "Window to Screen [01234567]." I guess it supports you having up to 8 monitors.

---

### Post by Jonathan2007 on 2010-03-19
@scallopedllama Awesome. Thanks so much. This is just what I have been needing for so long. I am glad someone helped me find it. :D

---

### Post by bohemier on 2010-05-19
> **wayfarer_boy said:**
> 
```
#!/bin/bash

offx=$( grep metamodes /etc/X11/xorg.conf | cut -d '+' -f 4 | sed 's/[^0-9]*//g' )
offy=$( grep metamodes /etc/X11/xorg.conf | cut -d '+' -f 5 | sed 's/[^0-9]*//g' )
curx=$(xwininfo -id `xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)"| cut -d ' ' -f 5` | grep "Absolute upper-left X" | cut -d ' ' -f 7)
cury=$(xwininfo -id `xprop -root | grep "_NET_ACTIVE_WINDOW(WINDOW)"| cut -d ' ' -f 5` | grep "Absolute upper-left Y" | cut -d ' ' -f 7)

if [ $curx -ge $offx ]
then
    newx=$((curx-offx))
    newy=$((cury-offy))
else
    newx=$((curx+offx))
    newy=$((cury+offy))
fi

/usr/bin/xdotool windowmove `/usr/bin/xdotool getwindowfocus` $newx $newy

exit 0
```
There's probably a better sed command to find the display resolutions (I'm definitely no sed guru - in fact, it's a tool I still find incredibly hard to use after years of wrangling with it) and when I use the script to move a window, repeated moves means the window slowly gets lower on each screen, so there's pixels being added to the newy value for some reason, but I can't work out why.

Anyway, let me know if this works for you.

Thanks wayfarer_boy! This works great! For hose who might have problems with the above script, make sure you remove these lines from your xorg.conf file:

```
# Removed Option "metamodes" .... 
```

they are automatically commented out by the nvidia tool but they hinder the script.

Cheers!

---

### Post by clockworkpc on 2010-09-06
Hi,

I'm having some problems with the newer script:

[COLOR="DarkRed"]clockworkpc@clockworkpc-laptop ~/Documents/Scripts $ ./move_window_to_other_display.sh
./move_window_to_other_display.sh: line 8: [: too many arguments
./move_window_to_other_display.sh: line 13: 1920
1920

1440: syntax error in expression (error token is "1920 1440")
usage: windowmove wid x y[/COLOR]

**System Details:**
Using Nvidia
Primary Monitor = 1440 * 900
Secondary Monitor = 1440 * 900 (to the right of Primary Monitor)

Effectively it's (0-1440)x900 and then (1441-2880)x900

Any ideas?

The original, simple script works beautifully though.  Thank you so much for this gem.

---

### Post by gfixler on 2010-11-21
I'll link an old post of mine that might have useful things for you guys (and others finding this thread) to dig through:

[http://ubuntuforums.org/showthread.php?t=815925](http://ubuntuforums.org/showthread.php?t=815925)

I have a 3-monitor system with 3 identical side-by-side monitors, but I'm also using a splitter box that makes them all look like one 3-wide monitor to one DVI plug from my video card. IOW, my computer sees one [3x 1280x1024 =] 3840x1024 screen, so each monitor's top left coords are 0,0, 1280,0, and 2560,0. I have Outputs set in Compiz to tell it where these logical boundaries are so I can max and fullscreen as usual. I'm using a bunch of things in the script to allow me to hotkey between monitors while retaining maximized and fullscreen status. I hooked them to Alt+h and Alt+l, as I use Vim, and character left/right hotkeys make sense for moving windows left and right.

---

### Post by I_am_nat on 2011-01-07
Thanks a lot! xdotool is just what I've been looking for.

---

### Post by renierm on 2011-04-05
Great script.

I have added a few things to make it more robust.

1. I have changed the grep statement to ignore the "Remove Option "metamodes" lines in some xorg.conf files.
2. I have added the ability to detect which CRT is the right most one. My system for some reason is CRT-0 and not CRT-1 as expected by the original script.
3. I have changed the way xprop is used so that the correct information is used when the words "_NET_ACTIVE_WINDOW" is in the "CUT_BUFFER" i.e. copy and paste in an app (emacs) returns this string a couple of times in xprop.
4. The window decoration causes the movement of the window lower in the screen so I have subtracted 27 for the theme that I am using. I don't have time now to figure out how to calculate this automatically.

I hope this helps


```
#!/bin/bash

offx_1=$( grep "^[[:space:]]*Option[[:space:]]*\"metamodes" /etc/X11/xorg.conf | cut -d '+' -f 2 | sed 's/[^0-9]*//g' )
offx_2=$( grep "^[[:space:]]*Option[[:space:]]*\"metamodes" /etc/X11/xorg.conf | cut -d '+' -f 4 | sed 's/[^0-9]*//g' )
offy_1=$( grep "^[[:space:]]*Option[[:space:]]*\"metamodes" /etc/X11/xorg.conf | cut -d '+' -f 3 | sed 's/[^0-9]*//g' )
offy_2=$( grep "^[[:space:]]*Option[[:space:]]*\"metamodes" /etc/X11/xorg.conf | cut -d '+' -f 5 | sed 's/[^0-9]*//g' )

if [ $offx_1 -gt $offx_2 ]
then
    offx=$offx_1
    offy=$offy_1
else
    offx=$offx_2
    offy=$offy_2
fi

curx=$(xwininfo -id `xprop -root _NET_ACTIVE_WINDOW | cut -d ' ' -f 5` | grep "Absolute upper-left X" | cut -d ' ' -f 7)
cury=$(xwininfo -id `xprop -root _NET_ACTIVE_WINDOW | cut -d ' ' -f 5` | grep "Absolute upper-left Y" | cut -d ' ' -f 7)

if [ $curx -ge $offx ]
then
    newx=$((curx-offx))
    newy=$((cury-offy-27))
else
    newx=$((curx+offx))
    newy=$((cury-offy-27))
fi

/usr/bin/xdotool windowmove `/usr/bin/xdotool getwindowfocus` $newx $newy

exit 0
```

---

### Post by mcsquared88 on 2011-05-24
This script doesn't work correctly if the two screens are different sizes and you're moving a maximized window. In my case, I have two monitors, one rotated to portrait. When I moved a maximized window from the landscape-mode monitor to the portrait-mode monitor, it would extend out across half of the landscape-mode monitor and the title bar would not be displayed.

I found a more complicated script at [http://my.opera.com/raphman/blog/show.dml/302528 ]("http://my.opera.com/raphman/blog/show.dml/302528")that handles maximized windows properly, but I had to modify the following lines to make it work on Ubuntu (11.04, at least) by changing the following lines:
```

# get window decor
xWinDecorLine=$(xprop -id $activeWinId | grep "_NET_FRAME_EXTENTS(CARDINAL)")
xWinDecor=${xWinDecorLine:37 :2}

```There's also a script at [https://github.com/younggift/argus/blob/master/monitor_switch.sh ]("https://github.com/younggift/argus/blob/master/monitor_switch.sh")that looks like it should work but I haven't tried it.

---

### Post by Fuertes::Benjami on 2011-08-13
Just what I needed. Thank you very much.

---

### Post by satish_vell on 2011-09-29
> **scallopedllama said:**
> For our friends on KDE 4: this is supported out of the box.

Open up System Settings > Keyboard and Mouse > Global Keyboard Shortcuts 

In there, pick the KDE Component KWin and the shortcuts in question are "Window to Screen [01234567]." I guess it supports you having up to 8 monitors.
That's exactly what I was looking a lot for, thank you.
Some how I couldn't find it when I was looking there.

---

### Post by dakster86 on 2011-10-25
I had this working beautifully (I think) under Ubuntu 11.04, but since upgrading to 11.10, I've noticed that windows that have had grid applied to them (e.g. ctrl+alt+KP_1) will no longer move with the tool. Indeed, if I just manually use the xdotool getactivewindow windowmove 100 100 variety of command, windows move just fine, but as soon as I use grid to align them, they stop. Anybody else having similar issues?

I've tried xprop to grab all the x properties of a "healthy" pregrid window and a "sick" postgrid window, and compared the output, and see nothing that would explain the inability of windowmove to work. Any ideas?

---

### Post by wayfarer_boy on 2011-10-26
> **dakster86 said:**
> I had this working beautifully (I think) under Ubuntu 11.04, but since upgrading to 11.10, I've noticed that windows that have had grid applied to them (e.g. ctrl+alt+KP_1) will no longer move with the tool. Indeed, if I just manually use the xdotool getactivewindow windowmove 100 100 variety of command, windows move just fine, but as soon as I use grid to align them, they stop. Anybody else having similar issues?

I've tried xprop to grab all the x properties of a "healthy" pregrid window and a "sick" postgrid window, and compared the output, and see nothing that would explain the inability of windowmove to work. Any ideas?

I don't have any ideas as to how to make this work again, but I'm wondering if the reason it isn't working is the same reason my devilspie configuration ([https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)) isn't working in 11.10. Could it be that Oneiric uses a flashy new Xorg to display windows that isn't backwards compatible with older Xorg tools (such as devilspie and xdotool)?

---

### Post by dakster86 on 2011-10-26
It seems that at least prior to invoking grid, xdotool and its various subfunctions perform well enough, but no longer after invoking grid. Perhaps it is an xorg issue, or perhaps it's something new with compiz (or just with grid)?

Any tips for other x tools that we could experiment with that might be lower level and more likely to work?

---

### Post by fraktalek on 2011-10-30
Great thread

I've tried  [https://github.com/younggift/argus/blob/master/monitor_switch.sh](https://github.com/younggift/argus/blob/master/monitor_switch.sh) 

but had to modify the following lines:

```
# window title bar height
# h_tbar=29
xWinDecorLine=$(xprop -id ${window} _NET_FRAME_EXTENTS)
h_tbar=${xWinDecorLine:37 :2}
if [ "x${h_tbar:1}" = "x," ]; then h_tbar=${h_tbar:0:1} ;fi 
```

Unfortunately it does not work after using the compiz "tiling shortcuts" Ctrl+Alt+<num>

---

### Post by Buurmas on 2011-12-05
> **fraktalek said:**
> Unfortunately it does not work after using the compiz "tiling shortcuts" Ctrl+Alt+<num>
Sorry for the off-topic interjection, but I was searching for the tiling shortcuts and found this thread. For the benefit of those who don't know about the tiling shortcuts, the "<num>" in your comment apparently has to be on the number pad. So, Ctrl+Alt+Numpad6 causes a window to occupy the right half of the current screen, but Ctrl+Alt+6 does nothing. Also, in "Keyboard Shortcuts" (Ubuntu 11.04 Unity), there are a few additional shortcuts, like Alt+F9 to minimize. Again, I apologize as this is off-topic.

---

### Post by ischurov on 2012-04-01
> **dakster86 said:**
> It seems that at least prior to invoking grid, xdotool and its various subfunctions perform well enough, but no longer after invoking grid. Perhaps it is an xorg issue, or perhaps it's something new with compiz (or just with grid)?

Any tips for other x tools that we could experiment with that might be lower level and more likely to work?
The same thing takes place after maximizing or semi-maximizing of the window. (And then restoring of course.) It seems to be Unity bug, not a Compiz or X one, because it is not reproduced under Gnome Shell at least. I filed a bug against Unity, see [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/971147](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/971147) for details.

---

### Post by suside on 2012-04-02
Zylion times easier method:

CCSM (Compiz Comfig Settings Manager) > Put > Put to next output

thanks to [http://www.only10types.com/2011/09/ubuntu-1004-lucid-keyboard-shortcut-to.html](http://www.only10types.com/2011/09/ubuntu-1004-lucid-keyboard-shortcut-to.html)

---

