---
title: "Hot keys to resize/reposition windows"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by tonkajeep34 on 2007-11-03
Hello,

Been using Ubuntu on and off for a little over a year and finally took the plunge and got rid of windows completely with 7.10. I have to say i love it, it's taken a little getting used to but it's been worth it.

One thing i do miss is a program called WinSplit Revolution ([http://reptils.free.fr/](http://reptils.free.fr/)). I have a widescreen monitor and it sets hot keys so that it will auto resize and move a window to a certain area of the screen.

e.g. ctrl+alt+1 puts a window in the lower left quadrant.

Does anyone know if there is a way to do something similar to this with Ubuntu, I've got compiz running with all the bells.

I seem to spend a lot of time putting a window on half the monitor so that i can see another on the other half....and i do use the other desktops too...

Thanks,
Mike

---

### Post by futz on 2007-11-03
> **tonkajeep34 said:**
> Does anyone know if there is a way to do something similar to this with Ubuntu, I've got compiz running with all the bells.
You can do part of that with compiz-fusion (or beryl). Not the resizing thing, but quickly placing a window in any of nine positions on the screen can be easily done.

In CompizConfig Settings Manager, go to Window Management and enable 'Put'.

To use it, use the Super key (Windows key) with keypad number keys.

---

### Post by tonkajeep34 on 2007-11-03
That's awesome... Thanks 

It's half the battle and makes it easier on these fancy new widescreen monitors

I like to keep a firefox window on the left half then a terminal and other misc. window split the right half...

---

### Post by spiregrain on 2008-04-03
There is a command called "wmctrl" available in the standard repositories, which can resize and place windows.  I've divided my 1680x1050 screen up into four sections, but made the left-hand column 1024 wide and the right-hand column 636 wide.  

Therefore the command to put the active window into the top-left quadrant is:

```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 1,2,0,1024,480
```

I've set up a similar command for top-right, bottom-right, bottom-left, left-hand-side and right-hand-side; and mapped them to super-insert, home, page-up, delete, end and page-down. (Using the Compiz Settings Manager's Commands page).

---

### Post by tonkajeep34 on 2008-04-21
spiregrain that's great. that's exactly what i wanted! Once i figure out the coordinates I'll map them like you did.

Thanks!

---

### Post by woodenfox on 2008-05-07
It Would be incredibly useful if you would post the scripts here please!
It's taking me hours to figure this out :(

It would be really nice if Compiz developed a feature like this, and added a maximize to half screen button next to the maximize button.

Big monitors are creating new neccecitys!

---

### Post by tonkajeep34 on 2008-05-09
WoodenFox I just did the same as spiregrain and mapped the command to a key

If you want to do this make sure you have wmctrl installed:

```
sudo aptitude install wmctrl
```

If you don't already have the Advanced desktop effects settings install it:

```
sudo aptitude install compizconfig-settings-manager
```

To open the Settings Manager, click System, mouseover Preferences and select Advanced Desktop Effects Settings. 

Click on general settings, Then the commands tab and fill out the command you want such as top left quarter of the screen in command0.

Click on the actions tab and map the bottom you want to command you want.

I used the following settings for a 1600x1200 monitor at work and it's not perfectly lined up but i felt it was good enough not to tweak it anymore. 

Enter a line into a terminal and change it to make it what you want before you put it into the command

Here's the ones i used for 1600x1200:
```
Top Left: 
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 1,2,0,800,555 
Bottom Left: 
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 1,2,600,800,575 
Left Side: 
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 1,2,0,800,1125 
Top Right: 
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 1,800,0,800,555 
Right Side: 
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 1,800,0,800,1125
Bottom right: 
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 1,800,600,800,575
```

---

### Post by steve9000 on 2008-07-07
I miss winsplit evolution too so I made a clone for compiz

See:
[http://suasol.wordpress.com/2008/06/28/new-tiling-plugin-for-compiz-fusion-grid/](http://suasol.wordpress.com/2008/06/28/new-tiling-plugin-for-compiz-fusion-grid/)

Announcement & discussion:
[http://forum.compiz-fusion.org/showthread.php?t=8821](http://forum.compiz-fusion.org/showthread.php?t=8821)

Enjoy,
Stephen.

---

