---
title: "How do I:  Turn Off Desktop Effects Via Terminal"
date: 2009-09-19
forum: Desktop Environments
---

### Post by foxmajik on 2009-09-19
**EDIT: **The Ubuntu project is aware of this bug.  It has been reported as [Bug 353126]("https://bugs.launchpad.net/vino/+bug/353126").

**EDIT: ** Marking the thread unsolved so it may be used for further discussion of the issue instead of posting more comments in the bug.

*If you are effected by this bug you should visit the bug report and mark yourself as affected by it.*

This will add weight to the bug.

System:
Ubuntu 9.04 Jaunty x64

Hello,

When "Desktop Effects" is enabled I cannot see updates to the desktop using the remote desktop application (Vino) -- it does not redraw after the initial frame is drawn.

I expect the cause of this is that output from the composite engine (Compiz Fusion) is not passed to Vino because it is rendered directly on the video card.

As a result, no screen updates are displayed in the VNC client.

I'd like to think I can access my desktop remotely without having to disable Desktop Effects every time I leave my desk.

I don't want to *remove* Compiz Fusion, I just want to switch it off temporarily so I can access my desktop using the remote desktop application.

I'd like to SSH into the machine and turn off Desktop Effects temporarily so I can connect with my VNC client.

**My question is:**

Is there any way to turn off Desktop Effects from the command line?

---

### Post by ubongo2008 on 2009-09-19
guess you are using metacity as wm  so just type ```
 killall -9 compiz.real ; metacity --replace 
```  EDIT:  if you are on a tty type   ```
 export DISPLAY=:0.0 ; killall -9 compiz.real ; metacity --replace 
```

---

### Post by foxmajik on 2009-09-19
> **ubongo2008 said:**
> guess you are using metacity as wm  so just type ```
 killall -9 compiz.real ; metacity --replace 
```  EDIT:  if you are on a tty type   ```
 export DISPLAY=:0.0 ; killall -9 compiz.real ; metacity --replace 
```

Is there a way to ask Compiz nicely to quit?

I don't like the idea of hard killing processes.

It seems like there should be a command line equivalent of clicking on "no desktop effects" in the "desktop" control panel window.

---

### Post by ubongo2008 on 2009-09-19
just leave out the killing command, will do what youwant   export DISPLAY=:0.0 ; metacity --replace

---

### Post by sherl0k on 2009-09-26
yeah if you do a metacity --replace then compiz will close gracefully, knowing that another wm has taken its place.

for the record there is to "solution" there are only "workarounds"

1. not using compiz at all
2. replacing compiz with metacity before connecting via vnc
3. running freenx (instead of vnc, which completely replaces the issue with vnc as a whole)

compiz doesn't work with vnc no matter what graphics card you have, be it nvidia, ati/amd, or intel. you can disable xdamage and run compiz in vnc but it's extremely slow.

---

### Post by silvagroup on 2009-09-27
> compiz doesn't work with vnc no matter what graphics card you have, be it nvidia, ati/amd, or intel. you can disable xdamage and run compiz in vnc but it's extremely slow. Very true, I have an Intel 4500 chipset and vnc compiz does not work with vnc. I ahve an nvidia chipset on my desktop w/o compiz and vnc works fine.

> running freenx (instead of vnc, which completely replaces the issue with vnc as a whole) haven't tried this because in Launchpad Bugs there seems to also be some problems w/freenx so this may nnot be the totla solution. I haven't tried it yet but will report on it as soon as I do.

---

### Post by llllskywalker on 2009-10-06
I have a "shortcut-hack" which i haven't seen as of yet either here or in the bug report discussions (perhaps i missed it).  You guys gave me the idea.  If you're like me and you have a slow connection and don't mind disabling compiz when you're vnc'ing, but still want to use compiz when you're at home, this one might work for you.  I'm a ubuntu newbie so maybe some of you scripters out there can improve this one.
 
Step 1) make two files on the desktop.  call the first one enable.sh and put this in it:
 
#!/bin/sh
compiz --replace
 
call the second one disable.sh and put this in it:
 
#!/bin/sh
metacity --replace
 
Step 2) right click on both files and go to Properties->Permissions and check "allow execution".
 
Step 3) drag both scripts to your menubar/taskbar thinggy. right click on them and change the icon to something you'll recognize (i used the two minesweeper gear ones) and name them enable/disable appropriately.
 
So you're at home and running with compiz and all is fine and dandy. Later at work you open a vnc connection (i use realvnc) and it opens up with a stale screen that won't refresh. However, the initial screen is valid and the mouseclicks still work. As long as you're not running an app in full-screen such that it covers up your menubar, you can click the disable icon and wala! - compiz is disabled and you have full control. you won't have all the compiz eyecandy, but then again most people run vnc with less colors and lower framerates anyway so it's not that big of a deal. When you get back home just click the enable icon and you get the idea...
 
If there was some way to write a background application that could hook into the vnc server - maybe monitor for the icon change or something, we could use that as a trigger to automatically detect when a vnc connection is made and then enable and disable compiz as clients connect and disconnect. But then again... i have a life ;-)  Besides - going through that much trouble would be harder than fixing the real problem. So until the Ubuntu guys get it fixed for real (soon i hope!), this hack will work for me. Since Ubuntu is free though, I won't complain :-)
 
--luke

---

### Post by llllskywalker on 2009-10-06
btw... i've been using this "shortcut workaround" for a while and i like it much better than the alternatives. unlike using freenx or a similar ssh system, you still get to log into an already open session. and unlike the noxdamage voodoo, you don't have to sacrifice lots of bandwidth. and it beats disabling compiz permanently.
 
i guess the disadvantage is that if you use full screen apps that cover the menubar you're screwed. the other bad part is that you don't get compiz when using vnc.
 
I'm not sure if it will work for everyone because i've only tested realvnc. it all depends on whether or not you can get that first screen to come up so you know where to click for the disable icon.

---

### Post by foxmajik on 2009-10-06
> **llllskywalker said:**
> btw... i've been using this "shortcut workaround" for a while and i like it much better than the alternatives. unlike using freenx or a similar ssh system, you still get to log into an already open session. and unlike the noxdamage voodoo, you don't have to sacrifice lots of bandwidth. and it beats disabling compiz permanently.
 
i guess the disadvantage is that if you use full screen apps that cover the menubar you're screwed. the other bad part is that you don't get compiz when using vnc.
 
I'm not sure if it will work for everyone because i've only tested realvnc. it all depends on whether or not you can get that first screen to come up so you know where to click for the disable icon.

It should work for the distro standard VNC.

Thanks for writing this -- I was thinking about writing something like it but I felt too lazy.  =)

Maj

---

### Post by koshari on 2009-10-19
> Step 1) make two files on the desktop.  call the first one enable.sh and put this in it:


nice workaround luke, 

alternatively you dont need 2 launchers you could use one with a little more code it can be a toggle effect , ie, click to on, click to off, ect.

i used a similar script for my wifi and bluetooth toggles on my lappie which i have adapted to this scenario. you basically have a hidden file that has a 1 or 0 value and depending on this the alternate state of the window manager.

so firstly create this file, 
```
echo 1 > ~/bin/.compizstate
```

then make the batch file which checks whe value of the hidden file and toggles the window manager accordingly,
this should be the go, 

```
#!/bin/bash
compizon=`cat ~/bin/.compizstate`
if [ $compizon = "0" ]; then
compiz --replace
echo 1 > ~/bin/.compizstate
else
metacity --replace
echo 0 > ~/bin/.compizstate
fi
```

place it in ~/bin so its in your path and can be callad from anywhere.

---

### Post by foxmajik on 2009-10-19
> **koshari said:**
> nice workaround luke, 

alternatively you dont need 2 launchers you could use one with a little more code it can be a toggle effect , ie, click to on, click to off, ect.

i used a similar script for my wifi and bluetooth toggles on my lappie, you basically have a hidden file that has a 1 or 0 value and depending on this the alternate commands are issued

this should be the go, 

```
#!/bin/bash
compizon=`cat /home/user/bin/.compizstate`
if [ $compizon = "0" ]; then
echo compiz --replace
echo 1 > /home/user/bin/.compizstate
else
echo metacity --replace
echo 0 > /home/user/bin/.compizstate
fi
```

obviously edit your username to reflect your home dir destination

When I switch back to Compiz all of my settings are reset to the default.

For example, when I am using Compiz I have the Grid plugin switched on and the Decorations plugin switched off, but when I switch to Metacity then back to Compiz, I have window decorations on again and the Grid plugin switched off.

Does anyone know how to make Compiz save settings between sessions?

---

### Post by llllskywalker on 2009-11-07
Hey that's a great idea koshari - it saves on shortcut real-estate. 
 
Is it just me, or did after upgrading to Ubuntu 9.10 did the "shortcut-solution" cease to work for other people too? Now when i try to turn off compiz via the shortcut over VNC the entire screen just goes to desktop background and Compiz doesn't disable like it used to.  Man this sucks... now I have to spend time finding some other hack to fix the VNC-Compiz bug that was introduced in 9.04. The -noxdamage fix won't work for me because I don't have enough bandwidth. When is this going to be fixed??!! I don't get why Ubuntu even bothers to add VNC to the distro if it's broken for the majority of us who enable visual effects?

---

### Post by llllskywalker on 2010-07-20
ubuntu 10.04 - still broken - awesome.

---

### Post by maniaq on 2010-09-25
...or just don't use vino - it's pretty ordinary

I use x11vnc and it works just fine - no problem with desktop effects or compiz or anything...

-and it's easier on the resources as well

---

### Post by Sword2 on 2012-03-21
Nobody asked, but since I was looking for it and took me a while to find...here is my "toggle":

```
qdbus org.kde.kwin /KWin org.kde.KWin.toggleCompositing
if [ $(qdbus org.kde.kwin /KWin org.kde.KWin.compositingActive) == "true" ]; then
	echo "Desktop compositing is ON"
else
	echo "Desktop Compositing is OFF"
fi
```

Enjoy!
:guitar:

---

