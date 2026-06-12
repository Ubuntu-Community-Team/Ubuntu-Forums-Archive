---
title: "placing windows in specific workspaces"
date: 2017-05-08
forum: Desktop Environments
---

### Post by Skaperen on 2017-05-08
a while back someone led me to workspace switching in unity.  how can i launch a program into a specific work space that i am currently not in.  i'm trying to automate a pre-launch of multiple workspaces.

---

### Post by deadflowr on 2017-05-09
Do you want the ability to open a new window in a different workspace whenever you open it, or do you mean you want to have certain apps always open in specific workspaces?

Not sure about the former, but to do the latter install ccsm (compizconfig-settings-manager), go to *Place Windows*, go to *Fixed Window Placement*, go to *Windows with fixed viewport*, click new to add the application you want to open in a specific workspace and set the x and y of the work space. Then when set every time you open that application, it will open in the designated workspace.
Rather crude, but works well for what it does.

---

### Post by Skaperen on 2017-05-09
when i launch an app from a shell command line or in a script.  the script might be running in the background but with DISPLAY set.  one problem i am seeing is that DISPLAY is the same in different workspaces so i have no idea how to refer to a specific workspace.  i do know X has a subdisplay numbering scheme although i ha never seen it used.  i was kind of expecting to see it used for workspaces, then i saw it was not used.

before i learned of workspaces, but when still using Unity, i used the menu at the gear icon to switch users as a kind of workspace switcher.  it is implemented as a rough X server switcher with all the X servers but one having their drivers disabled.  before i used Unity i used Slackware in mostly text mode with virtual consoles.  most systems have 12 virtual consoles and one gets used for X.  i remapped the keyboard to get 63 virtual consoles and used 3 of them for 3 instances of X. now that graphics is fast enough for things like heavy scrolling of large text windows i have switched to using graphics and now using Unity.

i am looking to build a better smoother workspace switcher by means of VNC.  the idea is each desktop/workspace is a VNC connection target.  hopefully a better VNC client will come along that can do a smooth clean switch, but if none does i am thinking of writing a VNC network switcher ... connect to it with any VNC client ... it connects to many VNC targets ... it adds buttons for clean one-click switching. i suspect by the time i do this, it will end up running in the cloud, connecting to cloud instances.

but for now i just want to be able to initialize a bunch of windows in the right places/workspaces.  i can do this where DISPLAY is different.

---

### Post by deadflowr on 2017-05-09
I'm fairly certain you can get a more nuanced control for workspace placements with wmctrl.
(I don't use it, but I've heard great things)

---

### Post by Skaperen on 2017-05-11
> **deadflowr said:**
> I'm fairly certain you can get a more nuanced control for workspace placements with wmctrl.
(I don't use it, but I've heard great things)
i don't see any means to open an app in a specific workspace.  i tried using some of its features but nothing worked (or even had any effect) so i removed it.

---

### Post by Skaperen on 2017-05-12
in "man x" there is:

[COLOR=#696969][FONT=courier new]        DISPLAY NAMES
                        From the user's perspective, every X server has a display name of the form:

                hostname:displaynumber.screennumber[/FONT][/COLOR]

and then:

        [COLOR=#696969][FONT=courier new]        screennumber

                Some displays share their input devices among two or more monitors.  These may be configured as a single logical screen, which allows  windows to move across screens, or as individual screens, each with their own set of windows.  If configured such that each monitor has its own set of windows, each screen is assigned a screen number (beginning at 0) when the X server for that display is started.[/FONT][/COLOR]

*screennumber* is not being regularly used.  so why can't we use that as a means to address or identify a specific workspace?  the concept is very much alike.

---

### Post by Skaperen on 2017-05-17
you can manually move windows between workspaces as if the workspaces were joined as one larger space.  but trying to open a window at a location off screen enough to be at a location in another workspace ends up with the window at the edge of the current workspace in that direction.

they just need to add support for multiple logical screen in the X server itself, including in the VNC version of X, with some user configurable keystroke sequence to switch screens.  this would be the obvious and simple solution.

---

### Post by again? on 2017-05-18
The issue with compiz is you really only have 1 desktop, no matter how many virtual workspaces you set.
For example I have a screen res of **1680x1050** and have configured compiz to have 2 horizontal virtual workspaces.
So what I really have is one desktop with a virtual resolution of **3360x1050**
_Viewport 1_
```
$ wmctrl -d
0  * DG: 3360x1050  **VP: 0,0**  WA: 49,24 1631x1026  N/A
```

_Viewport 2_
```
$ wmctrl -d
0  * DG: 3360x1050  **VP: 1680,0**  WA: 49,24 1631x1026  N/A
```

To move a window in a script you can use wmctrl to place a window at position x,y within the virtual desktop.
man wmctrl
> <MVARG>
A move and resize argument has the format 'g,x,y,w,h'. All five components are integers. The first value, g, is the gravity of the window, with 0 being the most common value (the default value for the window). Please see the EWMH specification for other values.
The four remaining values are a standard geometry specification: x,y is the position of the top left corner of the window, and w,h is the width and height of the window, with the exception that the value of -1 in any position is interpreted to mean that the current geometry value should not be modified.

So with my resolution I can use this to move firefox to viewport 2.
```
wmctrl -r "Firefox" -e 0,1680,-1,-1,-1
```
In a script you may have to wait for the firefox window to load before running the wmctrl move command.

The easiest way is to use the  **ccsm > window management > place windows** plugin as deadflowr showed.

---

