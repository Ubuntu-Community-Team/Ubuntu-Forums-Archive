---
title: "unity: how to launch a terminal window to s specific location"
date: 2018-03-31
forum: Desktop Environments
---

### Post by Skaperen on 2018-03-31
in unity i have already added terminal launchers and have configured them to specific sizes within the terminal program.  now what i want to do is make another launcher for one of those same sizes and configure it to launch the window at a specific geometry location.  i don't know the exact numbers i need, yet, but i can try different ones and see where i end up.

i have noticed that it tries to keep windows from overlapping when possible by moving from left to right until it can.  if there is a way for a specific launcher (the new terminal to be added) to make the window start at the right side and seek left to find a non-overlapping position, that would be another option, and might be a better option.

i have made a terminal that uses almost half the screen, full height and half width.  opening the 2nd such window leaves a smal vertical gap on the far right side and no gap in the middle.  i have been manually moving that window to the right so the gap is only in the center.  i want to make so i can click on one launcher then click on that new launcher and get two side-by-side terminal windows with the gap between them.

i am running Ubuntu Desktop Xenial 16.04.3 LTS as upgraded a few days ago on a System 76 laptop with a 1920x1080 display.

---

### Post by kerry_s on 2018-03-31
lol, if you you were using gnome it would be a cinch. just install a extension & you can have a tiling desktop. i use shellshape cause it can be set to auto do it, but there are others.
[ATTACH=CONFIG]279142[/ATTACH][ATTACH=CONFIG]279143[/ATTACH]

if all your doing is terminals, have a look at the help page: gnome-terminal --help

---

### Post by again? on 2018-03-31
In unity can't you achieve this with the compiz grid plugin?

---

### Post by Skaperen on 2018-04-01
i am using other window types, too.  the 2nd most common for me is Firefox (currently at version 59.0.2).  i usually run Firefox as a full size window (not fullscreen).  i view images with eog.  i dabble around with programs that do VNC stuff.   and i program some graphics in C and Python (and lots of other stuff).

i am open to the suggestion of another DE to use.  it must be possible to switch to it one user at a time.  i run my setup with 12 active logged-in users i switch around to using the gear icon in the far upper right corner.  any DE I will use must be compatible with this an be able to provide 6 or more soft workspaces sharing the same X server (i must be able carry copy-and-past among all of these).  if i try another DE then i am sure i will have a lot of questions.  but i will look around widely for answers (google, stackexchange, etc).

---

### Post by kerry_s on 2018-04-01
wow, so did you try the compiz plugin? 

any linux can do all that. it just boils down to preference. i'm sure unity can do what you want, just need to figure out the proper settings.

---

### Post by sudodus on 2018-04-01
There is a learning curve, but you can do a lot with **wmctrl**

---

### Post by Skaperen on 2018-04-01
> **kerry_s said:**
> wow, so did you try the compiz plugin? 

any linux can do all that. it just boils down to preference. i'm sure unity can do what you want, just need to figure out the proper settings.


no, but i do recall going over at least some of its documentation and got no impression it would do this.  i can get programs like xlogo and xclock to go where i want them to be with the -geometry option.  the following command puts xclock approximately where i want the 2nd terminal window to go:

[COLOR=#696969]**[FONT=courier\ new]xclock -geometry 900x1012+1018+0[/FONT]**[/COLOR]

but i need to find docs on how to do this with xterm.  i tried running xterm from my bashrc script when just the 1st terminal was created (to avoid a loop) but all i get is:

[COLOR=#696969]**[FONT=courier\ new]Non UTF-8 locale (ANSI_X3.4-1968) is not supported![/FONT]**[/COLOR]

which is not true (it is under a twin xterm and UTF-8 does work).

---

### Post by again? on 2018-04-01
xterm supports -geometry.
Place an xterm window to a size and position where you want it.
Run xwininfo and click on the xterm window.
The last line will show something like "-geometry 112x27+466+281"

Then xterm command would be
```
xterm -geometry 112x27+466+281
```

---

### Post by Skaperen on 2018-04-01
> **guber2 said:**
> xterm supports -geometry.
Place an xterm window to a size and position where you want it.
Run xwininfo and click on the xterm window.
The last line will show something like "-geometry 112x27+466+281"

Then xterm command would be
```
xterm -geometry 112x27+466+281
```

**[COLOR=#ff0000][FONT=courier\ new]xwininfo: error: Can't grab the mouse.[/FONT][/COLOR]**

the thing i don't already know, have not been able to find, and wonder if it is even possible in unity, is how to make one specific launcher button set that geometry.  i suspect it will be near 82x46+970+0.

---

### Post by again? on 2018-04-01
Do you want to move an existing terminal window to a certain position or
do you want launch a new terminal to a certain position?

---

### Post by Skaperen on 2018-04-01
> **guber2 said:**
> xterm supports -geometry.
Place an xterm window to a size and position where you want it.
Run xwininfo and click on the xterm window.
The last line will show something like "-geometry 112x27+466+281"

Then xterm command would be
```
xterm -geometry 112x27+466+281
```

what is running is not xterm.  it is /usr/lib/gnome-terminal/gnome-terminal-server which doesn't support -geometry.  the man page for gnome-terminal shows --geomtry (two - characters).  that doesn't work either.  maybe it's time to change terminal program and avoid Gnome stuff.

---

### Post by Skaperen on 2018-04-01
> **guber2 said:**
> Do you want to move an existing terminal window to a certain position or
do you want launch a new terminal to a certain position?

i want to configure a launcher button to start the terminal program so that opens its window at a specific location _OR_ have it start looking for a place to open the window at the right side instead of the left side (which is the default).  i want to have, as an end result, two terminal programs side-by-side, NOT butted up right next to each other (leave at least 8 pixels of gap).

right now if i click the one button i have configured for an 82x46 terminal, twice, the 1st window opens as far left as possible and the 2nd window opens as far left as it can without overlapping, which is way to the right with about 30 pixels of space on the far right.  i want to get the 2nd terminal further right without having to manually move it.  a solution with 2 separate buttons is fine.  a solution that fails with more than 2 windows per workspace is fine (i am only going to open 2 terminal windows in workspaces that i do this in)

---

### Post by again? on 2018-04-01
You specified xterm.
> **Skaperen said:**
> ....but i need to find docs on how to do this with xterm......

gnome-terminal uses a double dash with geometry.
```
gnome-terminal --geometry 82x46+970+0
```

---

### Post by kerry_s on 2018-04-01
here's a thought, just tossing it out after playing with ubuntu-budgie.

how about a single terminal that can do multiple tiles? from what i read, tilix terminal is customize-able.
[https://itsfoss.com/tilix-terminal-emulator/](https://itsfoss.com/tilix-terminal-emulator/)

for you multitasking power users. lol :)

---

### Post by again? on 2018-04-01
I think I see what you mean though.
I booted into unity and created 2 quicklist items to launch a left and right terminal side by side
but the left terminal doesn't want to position to the right edge.
Watch video----> [https://streamable.com/gu67k](https://streamable.com/gu67k)

I'll keep playing around to see if I can get a term to position correctly.

**[COLOR="#FF0000"]Edit:[/COLOR]** I found if I use separate profiles for each terminal they position properly.
I created the profiles termL and termR.
[ATTACH=CONFIG]279157[/ATTACH]

Then used these commands:
_termL_
```
gnome-terminal --window-with-profile=termL --geometry 121x54+41+0
```

_termR_
```
gnome-terminal --window-with-profile=termR --geometry 58x54-4+0
```

Video ----> [https://streamable.com/ulajh](https://streamable.com/ulajh)

---

### Post by again? on 2018-04-02
You can disregard the profiles although it doesn't hurt to use different profiles as you can use different color schemes.
I had changed the initial terminal size in the profiles which appears to be the fix.
Change the "initial terminal size" to the lowest setting.

---

### Post by Skaperen on 2018-04-04
[QUOTE=guber2;13753254]You specified xterm.

i was speaking generically at first.  i discovered which exact program later on.  sorry for the confusion.  my previous experience with X windows is from before Ubunutu.  back then, any program emulating a terminal on X windows was named xterm and systems with more than one would use that name as a redirection point (symlink).

given the incorrect options of the gnome program, i am looking into an overall switch of terminal emulator.  or may i need to switch to a new DE.

---

### Post by Skaperen on 2018-04-04
> **kerry_s said:**
> here's a thought, just tossing it out after playing with ubuntu-budgie.

how about a single terminal that can do multiple tiles? from what i read, tilix terminal is customize-able.
[https://itsfoss.com/tilix-terminal-emulator/](https://itsfoss.com/tilix-terminal-emulator/)

for you multitasking power users. lol :)

that seems like a possible way.  so, how do i set up a Unity launcher button to launch one with the desired setup ... not fullscreen but takes up as much of the window space as it can ... two virtual terminals, side by side.

---

### Post by Skaperen on 2018-04-04
> **guber2 said:**
> 
Video ----> [https://streamable.com/ulajh](https://streamable.com/ulajh)

i was waiting to see one button action open both terminals.

---

### Post by again? on 2018-04-04
Between this and the other thread I thought you would have enough info to work something out.
I'm using xfce4-terminal so I can use the title flag.
Example:
_**/home/glen/.local/share/applications/tiled-terminals.desktop**_ (custom icon attached)(edit for your paths)
```
[Desktop Entry]
Name=Tiled Terminals
Comment=Terminal Emulator
Exec=/home/glen/scripts/aatest.sh
Icon=/media/Data/glen/Pictures/icons/tiling-terminal.png
Terminal=false
Type=Application
Categories=GTK;System;TerminalEmulator;
StartupNotify=true
```

**_/home/glen/scripts/aatest.sh_** (edit for your custom sizes)
```
#!/bin/bash
xfce4-terminal --title=termL --geometry 94x52+39--13 &
xfce4-terminal --title=termR --geometry 67x52--10--13
```

Using a 3x3 desktop, edit **ccsm > window management > place windows** to open
terminals of title termR or termL on workspace 2.
```
title=termL | title=termR
```
[ATTACH=CONFIG]279176[/ATTACH]

Left clicking launcher opens 2 xfce4-terminals of custom position and size.
For normal terminals use the default gnome-terminal launcher.
vid---> [https://streamable.com/wu2xs](https://streamable.com/wu2xs)

---

