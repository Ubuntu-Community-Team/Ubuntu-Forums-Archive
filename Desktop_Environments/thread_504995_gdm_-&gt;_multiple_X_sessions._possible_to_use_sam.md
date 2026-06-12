---
title: "gdm -&gt; multiple X sessions. possible to use same user?"
date: 2007-07-19
forum: Desktop Environments
---

### Post by pocketninja on 2007-07-19
Hey folks,
[I][B][SIZE="2"]
Synopsis:[/SIZE][/B][/I]
I have the need for multiple X sessions with different screen configurations. Wine seems pretty good at HL2 and other games now; the only issue is that it doesn't seem to like the way I have my dual screen set up configured. Eg, HL2 picks it up as a "widescreen configuration", and has some other side effects as a result: no bloom, not saving config options, etc. That's not all too relevant tho. I've tested and proved this. A single screen setup does not have these issues on my system. =)

***[SIZE="2"]Question:[/SIZE]***
For the best part I've been successful. I can now hit Ctrl+Alt+F9 to switch to an X session which uses only one screen. **Only issue now, is that if I log in with my default username in one X session I can't use it in the other. Is it possible to use the same username over multiple X sessions?**



***[SIZE="2"]Steps/Details relevant to above:[/SIZE]***
Assuming you're using Ubuntu (not Kubuntu??), and are using the the stock gdm configuration, here's how I've achieved multiple X sessions, with different screen configurations (xorg.conf ServerLayouts):
[LIST=1]
[*]Backup* /etc/gdm/gdm.conf*
[*]Open */etc/gdm/gdm.conf* using your editor of choice 
```
sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf.20070719
sudo vim /etc/gdm/gdm.conf
```
[*]Find the *[servers]* section
[*]Where it says ```
0=Standard
``` add a new line after it with ```
1=SingleScreen
```
[*]Find the *[server-Standard]* section
[*]Duplicate the entire *[server-Standard]* section, with the name *[server-SingleScreen]*
[*]added ```
-layout SingleScreen
``` to the command option.
Before the change the line should look something like ```
command=/usr/X11R6/bin/X -br -audit 0
```
[*]All up, the changes in gdm.conf should look a bit like this:
```

[servers]
0=Standard
1=SingleScreen

...

[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0
flexible=true

[server-SingleScreen]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 -layout SingleScreen
flexible=true

...


```
[*]Save and close
[*]Backup, then open in your editor of choice */etc/X11/xorg.conf*
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.20070719
sudo vim /etc/X11/xorg.conf
```
[*]Copy the existing "*ServerLayout*" Section and put the copy AFTER the existing one
[*]Change the value of "*Identifier*" of the copied "*ServerLayout*" to "*SingleScreen*"
[*]Remove any options that weren't required (such as Xinerama)
It should look something a bit like 
```
Section "ServerLayout"
        Identifier      "SingleScreen"
        Screen          "Single Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

```
[*]Change the "*Screen*" option to: Screen "*Single Screen*"
[*]Copy the "*Screen*" section for the screen device you want to use
[*]Change the Screen's "Identifier" value to "*Single Screen*"
[*]Remove options that weren't required (such as Xinerama, for some people, and MetaModes)
[*]Should look something like:
```
Section "Screen"
        Identifier      "Single Screen"
        Device          "Generic Video Card" #This might be different for you
        Monitor         "CPD-E230" #This might be different for you
        Defaultdepth    24
        SubSection "Display"   #this section may be a little different too, depends on your existing config
                Depth   24
                Modes   "1280x1024" "1024x768" "800x600"  
        EndSubSection
EndSection
```
[*]Save, quit, and restart gdm: ```
sudo /etc/init.d/gdm restart
```
[/LIST]

Should now be able to use Ctrl+Alt+F7 and Ctrl+Alt+F9 to switch between sessions. It might be f8 in your case? For some reason f9 was automatically allocated for me.

:)

Any thoughts?

---

