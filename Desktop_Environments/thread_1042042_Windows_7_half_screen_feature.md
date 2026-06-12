---
title: "Windows 7 half screen feature"
date: 2009-01-17
forum: Desktop Environments
---

### Post by Niksko on 2009-01-17
Is it possible to emulate the feature of Windows 7 whereby you drag a window to the left or right of the screen and it resizes to take up that half of the screen?

Is this already possible or does it require some fiddling? (a shell script for example)

Thanks

-Nik

---

### Post by johnjohn2 on 2009-01-17
I like the idea

Bump

:guitar:

---

### Post by damis648 on 2009-01-17
As good an idea as that is, it won't work very well for people with multiple workspaces.

---

### Post by Niksko on 2009-01-17
Why the issue with multiple workspaces?

Also is there any promise in using the --geometry flag?

---

### Post by Niksko on 2009-01-18
May have found a solution.
I'm thinking of using the wmctrl program to move and resize the window. Now all I need to do is incorporate some hotkeys (I'm thinking <ctrl><super><left/right> and then you click on the window) and I'll be set.

I'll post back if I get it working.

Edit: Might take longer than expected, as wmctrl doesn't want to behave

---

### Post by Niksko on 2009-01-18
All done. Found some other resources that were trying to do a similar thing and adapted from that.

Here's how I did it:

You need to install wmctrl first using "sudo apt-get install wmctrl"

Download the scripts that I've attached. I put the scripts in ~/bin. I used the command feature of Compiz (under general settings) to setup hotkeys for each script. In my case, this was ~/bin/rightdock.sh and ~/bin/leftdock.sh.

You'll need to edit the scripts to match your screen resolution and some other things, but all the instructions are included in the script.

Hope it works for you and pm me if you have any problems.

It's turned out really well for me. Works just like I wanted it to. Plus, now I know how to use wmctrl :D

-Nik

-PS Take THAT Windows 7
-PPS One last thing. This also works for dual screen setups using Twinview like I am. Again, instructions are in the scripts

---

### Post by homburg on 2009-01-19
I use GridMove for windows xp at my work and have looked for this feature for Ubuntu/Gnome for a while.

I've made som minor changes to the script. Mainly using xrandr to read the resolutions and offsets.

Too lazy to update the comments, though :-)

I have tested this on metacity without compositing and native multi-monitor (not nvidia twinview).

---

### Post by zhocchao on 2009-01-19
As I hope to catch some interest for a project (more than half screen feature).
[http://ubuntuforums.org/showthread.php?p=6579904](http://ubuntuforums.org/showthread.php?p=6579904)


g
z

---

### Post by linbeans on 2009-01-19
> **damis648 said:**
> As good an idea as that is, it won't work very well for people with multiple workspaces.

That would be a good place to start.. Getting to view multiple desktops within the same screen. I'm not sure if there's something similar in KDE

---

### Post by soccermonster5 on 2009-01-29
> **homburg said:**
> I use GridMove for windows xp at my work and have looked for this feature for Ubuntu/Gnome for a while.

I've made som minor changes to the script. Mainly using xrandr to read the resolutions and offsets.

Too lazy to update the comments, though :-)

I have tested this on metacity without compositing and native multi-monitor (not nvidia twinview).


Looking at this script, it seems that for my configuration the sed commands don't prune the output of xrandr quite right.  Running your commands, I get an extra line I think wasn't meant to be there:

```

sean@seans-laptop:~$ xrandr | sed -e '/connected/!d' -e "s/.*connected\s\([0-9]*\)x\([0-9]*\)+\([0-9]*\)+\([0-9]*\).*/\1\n\2\n\3\n\4/"
1680
1050
0
0
DVI-0 disconnected (normal left inverted right x axis y axis)
1280
800
1680
250
```

I'm no expert on sed by any means, but I fixed it like so:

```
sean@seans-laptop:~$ xrandr | sed -e '/[^s]connected/!d' -e "s/.*connected\s\([0-9]*\)x\([0-9]*\)+\([0-9]*\)+\([0-9]*\).*/\1\n\2\n\3\n\4/"
1680
1050
0
0
1280
800
1680
250
```

I just put the [^s] in there so it wouldn't match "disconnected."  There may be a more appropriate solution, but like I said, I don't know enough about sed to think of anything better, and this works for me ;)

EDIT:

I've made a few changes of my own to the script, including what I've mentioned above.  Also, it was incorrectly assuming which monitor was on the left, and which was on the right, so I put in a check to see that screen0xoffset is 0.  If it isn't, then it swaps the two screens.  So now, it should autodetect anyone's monitor layout, hopefully.  One last thing I changed was to make it maximize the vertical component of the window to the vertical size of the screen measured initially (which it does not seem to do fully, anyway), not to be done automatically by wmctrl using maximized_vert, as homburg had it do.  I found that I wasn't able to resize the window vertically after the script is run using maximized_vert, and it was very frustrating to me.  I also changed it so that framecomp was added to the x position of a window being put on the right instead of subtracted, so that 2 windows maximized next to each other on the same screen won't overlap (if you set the right framecomp).  I'm adding the new script, if nobody minds.  I also added a few comments :)

EDIT2:

Script now supports maximizing windows to take up the top or bottom half of the screen as well.  Just pass it up or down as an argument.

---

### Post by lfsrteixeira on 2009-02-25
The Windows 7 half screen feature is one that is really really useful for widescreeners. I really find it a simple and useful idea, even if it was "borrowed" from someone else, as M$ sometimes do. I would like to have similar functionality in my Ubuntu, and you are doing a great job on it. Thanks for the scripts!

On the other hand, the W7 functionality is more "complete", in the sense that an docked window can be restored to their original position and size by dragging it from the border. I think it is more difficult to implement, you should "memorize" the older position of docked windows. And the W7 solution has the added benefit that you don't have to remember a key combination to make it work - that is user friendlier... I personally have no problem with key combinations, but many people don't like it.

Hope that your solution gets incorporated into compiz, and that then it evolves to get even better than the W7 solution!

---

### Post by philg88 on 2009-09-28
Under CCSM you can use the Grid plugin and set hotkeys for "Put Left" and "Put Right"; there's options for center, bottom, top, top right, etc.

---

### Post by rrob on 2010-02-16
> **philg88 said:**
> Under CCSM you can use the Grid plugin and set hotkeys for "Put Left" and "Put Right"; there's options for center, bottom, top, top right, etc.

Great function - it works easy without any scripts - just enable grid in compiz settings and use Ctrl+Alt+KP1 ... 9. Yes, draging to edge didnt work and it could be in conflict with draging window to diferent screen. Solution could be combination of draging windows with holding some button.

---

### Post by stinkeye on 2010-02-16
[**_[COLOR="DarkRed"]aero-snap-ubuntu[/COLOR]_**]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html")

---

### Post by Rellix999 on 2010-04-16
delete-me

---

### Post by andrea000 on 2010-04-16
Here is another way to do it compiz has had this
for sometime now.

> sudo apt-get install compizconfig-settings-manager wmctrl
Open Compiz Config Settings Manager select
the Commands option.

In  'Command Line 0' paste
> WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1
In Command Line 1 paste
> WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x'` && HALF=$(($WIDTH/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1
And in Command Line 2 paste
> wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
Now choose the Edge Bindings tab at the top and set
> Run Command 0 - Set To Left
> Run Command 1 - Set To Right
> Run Command 2 - Set To Top

Set the 'Edge Trigger Delay' to something around
400 to 500 by dragging the slider to the right.
drag a window to one of the specified sides and your
window will automatically resize if your using compiz
cube then this way will not work and the grid plugin
may be better.

---

### Post by drewster1829 on 2010-05-31
> **lfsrteixeira said:**
> 
On the other hand, the W7 functionality is more "complete", in the sense that an docked window can be restored to their original position and size by dragging it from the border. I think it is more difficult to implement, you should "memorize" the older position of docked windows. And the W7 solution has the added benefit that you don't have to remember a key combination to make it work - that is user friendlier... I personally have no problem with key combinations, but many people don't like it.

I'm using andrea00's instructions, but using edge bindings topleft, topright, and top (so as not to interfere with my edge bindings for rotate cube), and thus I don't have to memorize any key combinations.

Also, after resizing, by maximizing then unmaximizing, my window gets restored to its original size and position before half-screening it, so take **that**, Windows 7. :)

Thanks again...I learned about the Windows 7 Aero feature after I had a friend who complained about it (he uses multiple monitors, not widescreen, so to him it was an annoyance, not an advantage), and I thought "Wow!  Wouldn't that be cool if I could do it in Ubuntu on my widescreen monitor?"  It's way handier than resizing them by hand, that's for sure.

---

### Post by ABaconBusAflame on 2010-11-29
[COLOR="Red"]**A quick note for those following the instructions in andrea000's post:**[/COLOR]

When using the side-snapping feature, your windows may not take up exactly half of the screen. For example, when snapping windows to the right, the window might take up half of the screen and a few pixels of the left side of the desktop to the right. Also, left-snapped windows may tend to overlap your right-snapped windows by a few pixels.

To fix this, replace the "HALF=$(($WIDTH/2))" equation in "Command Line 0" and "Command Line 1" with something like "HALF=$(($WIDTH/2**-3**))" This "-3" value will decrease the "HALF" value slightly, giving you slightly skinnier windows.

However, keep in mind that a value of "-3" might not work for everyone (or even both "Command Line 1" and "Command Line 0"). For example, my "Command Line 0" looks like this:

> WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x' `&& HALF=$(($WIDTH/2**-9**)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$HALF,-1

while my "Command Line 1" looks like this:

> WIDTH=`xdpyinfo | grep 'dimensions:' | cut -f 2 -d ':' | cut -f 1 -d 'x' `&& HALF=$(($WIDTH/2**-3**)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$HALF,0,$HALF,-1

I suggest fiddling around with the "HALF" values until they provide the desired result for your setup.

---

### Post by inobe on 2010-11-29
this is default in kubuntu

---

### Post by Aleks@orohena on 2011-12-27
Hi all,

I wrote a script that uses wmctrl. Copy it to the directory of your choice, e.g. $HOME/bin (it has to be listed in the PATH variable).  Then, for each of the accepted script names, create a symbolic link to the script.

```

cd $HOME/bin
mv $DOWNLOAD/winctrl .
ln -s winctrl winctrl-north
ln -s winctrl winctrl-south
ln -s winctrl winctrl-west
ln -s winctrl winctrl-east
ln -s winctrl winctrl-nw
ln -s winctrl winctrl-ne
ln -s winctrl winctrl-sw
ln -s winctrl winctrl-se

```

Then, calling the script by one of the names starting with winctrl- will resize and reposition the currently active window according to the calling name.

The only thing I haven't found out yet is how to automatically compute FRAME_CORRECTION_X (total number of pixels occupied by left and right window borders) and FRAME_CORRECTION_Y (total number of pixels occupied by top and bottom window borders).  You'll have to fix those for your window manager settings.

The script's code:

```

#!/bin/bash
# winctrl
# http://www.aczutro.de

FRAME_CORRECTION_X='8'
FRAME_CORRECTION_Y='27'

FULL_GEOM=`wmctrl -d | grep '\*' | awk '{print $9}'`

FULL_X=`echo $FULL_GEOM | cut -dx -f1`
FULL_Y=`echo $FULL_GEOM | cut -dx -f2`

let 'HALF_X	= FULL_X / 2'
let 'HALF_Y	= FULL_Y / 2'
let 'BIG_X	= FULL_X / 3 * 2'
let 'SMALL_X	= FULL_X - BIG_X'

let 'HALF_X_CORR	= HALF_X	- FRAME_CORRECTION_X'
let 'HALF_Y_CORR	= HALF_Y	- FRAME_CORRECTION_Y'
let 'BIG_X_CORR		= BIG_X		- FRAME_CORRECTION_X'
let 'SMALL_X_CORR	= SMALL_X	- FRAME_CORRECTION_X'

case `basename $0` in
    winctrl-west)
        NEWSIZE=4,0,0,$HALF_X_CORR,-1
        ADDPROP=maximized_vert
        ;;
    winctrl-east)
        NEWSIZE=6,$FULL_X,0,$HALF_X_CORR,-1
        ADDPROP=maximized_vert
        ;;
    winctrl-north)
        NEWSIZE=2,0,0,-1,$HALF_Y_CORR
        ADDPROP=maximized_horz
        ;;
    winctrl-south)
        NEWSIZE=8,0,$FULL_Y,-1,$HALF_Y_CORR
        ADDPROP=maximized_horz
        ;;
    winctrl-nw)
        NEWSIZE=1,0,0,$HALF_X_CORR,$HALF_Y_CORR
        ADDPROP=maximized_dummy
        ;;
    winctrl-ne)
        NEWSIZE=3,$FULL_X,0,$HALF_X_CORR,$HALF_Y_CORR
        ADDPROP=maximized_dummy
        ;;
    winctrl-sw)
        NEWSIZE=7,0,$FULL_Y,$HALF_X_CORR,$HALF_Y_CORR
        ADDPROP=maximized_dummy
        ;;
    winctrl-se)
        NEWSIZE=9,$FULL_X,$FULL_Y,$HALF_X_CORR,$HALF_Y_CORR
        ADDPROP=maximized_dummy
        ;;
    winctrl-big-left)
        NEWSIZE=4,0,0,$BIG_X_CORR,-1
        ADDPROP=maximized_vert
        ;;
    winctrl-small-right)
        NEWSIZE=6,$FULL_X,0,$SMALL_X_CORR,-1
        ADDPROP=maximized_vert
        ;;
    *)
        exit 1
esac

WMCTRL='wmctrl -r :ACTIVE:'

$WMCTRL -b remove,maximized_vert,maximized_horz
$WMCTRL -e $NEWSIZE
$WMCTRL -b add,$ADDPROP

```

---

