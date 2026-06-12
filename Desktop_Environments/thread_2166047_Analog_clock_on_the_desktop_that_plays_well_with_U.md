---
title: "Analog clock on the desktop that plays well with Unity"
date: 2013-08-07
forum: Desktop Environments
---

### Post by joni8135 on 2013-08-07
I have just a newly installed 12.04LTS 64bit and come from 10.04LTS 32-bit. I'm found of cairo-clock or Macslow's cairo-clock, an analoug clock for the desktop. But when I add cairo-clock to 'Startup applications', the clock have sometimes grafical errors, like a 1/4 of the clock are shown. It get fixed by open settings an change some size parameters. But another more serious problem is that the minute pointer can lag for over 5 minutes, compared to systemtime and that lead to that I missed my bus this morning :(

Is there any other analog clock for the desktop in 12.04LTS?

Thanx for any tip!

---

### Post by sudodus on 2013-08-07
There are so many of them ...

Try one of the very simplest ones from the old Unix days: ***xclock*** and ***oclock***,

or try this one [http://pwet.fr/man/linux/commandes/swisswatch](http://pwet.fr/man/linux/commandes/swisswatch)

I think ***xclock*** and ***oclock ***need very little horsepower, and they should not lag, but SwissWatch looks better. Maybe it will not lag for you. Try them out!

---

### Post by joni8135 on 2013-08-07
Thanx

---

### Post by stinkeye on 2013-08-08
You could also run a conky clock.
Install conky...
```
sudo apt-get install conky-all
```

Extract the **conky_analog_clock.tar.gz** attachment and then press ctrl+h to reveal the hidden folder "**.conky**"
Move this folder to your home directory.

Open a terminal and run...
```
conky -c ~/.conky/analog_clock/conkyrc
```

The clock has 27 different clockfaces.
To cycle through the different clockfaces, in another terminal run...
```
~/.conky/analog_clock/choice.sh
```
Press ctrl+c to stop the choice.sh script and use the current clockface.

To change the screen position, open ~/.conky/analog_clock/conkyrc in your text editor
and adjust these values...
```
gap_x [COLOR="#FF0000"]10[/COLOR]    ## left &right
gap_y [COLOR="#FF0000"]80[/COLOR]   ## up & down

alignment [COLOR="#FF0000"]tr[/COLOR]
```

From man conky...
> **gap_x** 
Gap, in pixels, between right or left border of screen, same as passing -x at command line, e.g. gap_x 10.  For other position related stuff, see 'alignment'.

**gap_y**  
Gap, in pixels, between top or bottom border of screen, same as passing -y at command line, e.g. gap_y 10.  For other position related stuff, see 'alignment'.

**alignment**
Aligned  position  on  screen, may be top_left, top_right, top_middle, bottom_left, bottom_right, bottom_middle, middle_left, middle_middle, middle_right, or none
              (also can be abreviated as tl, tr, tm, bl, br, bm, ml, mm, mr). See also gap_x and gap_y.

Add this command to startup applications to autostart ("-p 15" pauses start for 15 secs...needed for some window managers)
```
sh -c "conky -p 15 -c ~/.conky/analog_clock/conkyrc"
```

---

