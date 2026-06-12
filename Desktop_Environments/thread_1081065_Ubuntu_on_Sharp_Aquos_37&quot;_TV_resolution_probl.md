---
title: "Ubuntu on Sharp Aquos 37&quot; TV resolution problem"
date: 2009-02-26
forum: Desktop Environments
---

### Post by 192.168.0.1 on 2009-02-26
Hey all,

Got ubuntu installed on my new (made up of old parts i had lying around) HTPC today.

Had some issues during installing because the screen was all weird and cut off parts of the dialogue boxes so couldn't read/fill in some fields.. got through that by plugging the computer into a normal monitor.

Anyway, have switched over to the TV now, and it's all going good.

EXCEPT I can't see the top and bottom of the screen.

The resolution is set to 1920x1080. The picture is clear and looks fine (it's plugged into the DVI port on the graphics card, and then into the HDMI port on the TV), but I can't see the menu's etc up the top, or the bar down the bottom.

I can move the mouse up there and open up the menus etc. But I don't know what i'm clicking on as I can't see it!!!

I've tried changing the resolution.. doesn't help.

The resolution for the TV should be 1366 x 768, I've tried all the combinations available in the nvidia chipset drivers (and i downloaded the new recommended drivers) and still not working...

any ideas?

graphics card is a geforce 6200

Thank you!!!

EDIT: should also mention i'm a complete Linux newb :(

---

### Post by 192.168.0.1 on 2009-02-26
any ideas?

I don't get this problem on an windows XP installation, and I really don't want to go back to windows for this machine :S I like ubunutu (have it on my laptop), and really don't want to go back.

Have I posted in the wrong forum perhaps?

---

### Post by hartmann on 2009-02-26
I have a 37' sharp Aquos (1080p) and I have the opposite problem.

Instead of overscanning the image I get underscan and black boarders around the edge of the screen. I can fix it but its a pain in the ***, but I also have some other problems not related to the display (catalyst 9.2 drivers and the HD 4870 1gb).

In your situation I bet the problem is the TV settings.

At the bottom of the remote control there is a flip down panel. Open it and press the "av mode" button. Set this to "user".

Press the "view mode" button on the top of the remote and select "dot by dot".

This will allow the incoming image to be displayed unaltered.

---

### Post by 192.168.0.1 on 2009-02-27
thanks for the reply!!!

I'll give that a go tonight when i get home!

Thanks mate!

---

### Post by 192.168.0.1 on 2009-02-27
hey mate,

I had a look through the manual and all over the remote and I can't find a "view mode" button on the remote at all... and no options for dot by dot either :(

Also, the input i'm using, which is the only HDMI input available (and is named input 4 atm), has a number of options unavailable.

For example when i press the "wide" button (which is next to "av mode") i have no options, its just set to "full" and i can't change it. But with all the other inputs and regular tv channels i can change it to a number of different settings.

Also when i hit menu, there is a lot more options for every other channel and input then there is for input 4 (the hdmi input)...

Ideas? :( :( :(

Thanks for your suggestion... if i could find this "view mode" button it may even work.... :S

---

### Post by orethrius on 2009-02-27
This is more of a workaround than a real fix, but it may be worth trying.

Hold Alt and hit F2, then type **gnome-terminal** and hit enter to open a terminal.

Type in **xrandr** and hit enter to display a list of available resolutions.  In my laptop's case, I get this:
```
oem@amoktime:~$ xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900       60.0* 
   1280x800       60.0  
   1280x768       60.0  
   1152x864       60.0  
   1024x768       60.0  
   848x480        60.0  
   800x600        60.0  
   720x576        60.0  
   720x480        60.0  
   640x480        60.0  
   640x400        60.0  
   640x350        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0 
```

What you want to do is find the line that either says 1366 x 768, or - if that is unavailable - find the closest available resolution without going over (in my case, 1280x800 were 1440x900 not available).  In that Terminal that you still have open (it *is* still open, right? ;)) type this:
```
xrandr -s yoursizehere
```
and hit enter.

I call this a workaround because it's not permanent across sessions, and will have to be re-done each time you reboot.

There is undoubtedly a line in xorg.conf that can be configured to handle this, but it's late and I have work soon.  Sorry I couldn't be of more help.

---

