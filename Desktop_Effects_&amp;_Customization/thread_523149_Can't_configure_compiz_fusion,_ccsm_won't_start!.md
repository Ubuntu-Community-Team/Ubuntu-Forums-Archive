---
title: "Can't configure compiz fusion, ccsm won't start!"
date: 2007-08-11
forum: Desktop Effects &amp; Customization
---

### Post by era506 on 2007-08-11
Hi everyone!

I just install compiz fusion and it is working great except for one thing: compizconfig settings manager won't start, the icon on System->Preferences has disappeared and when I try to run it writing "ccsm" in terminal the following text appear: 

```
era506@era506-desktop:~$ ccsm
Backend     : gconf
Integration : true
Profile     : default
Adding plugin fs (Userspace File System)
Adding plugin extrawm (Extra WM Actions)
Adding plugin text (Text)
Adding plugin reflex (Reflection)
Adding plugin showdesktop (Show desktop)
Adding plugin addhelper (ADD Helper)
Adding plugin shift (Shift Switcher)
Adding plugin scalefilter (Scale Window Title Filter)
Adding plugin thumbnail (Window Previews)
Adding plugin splash (Splash)
Adding plugin neg (Negative)
Adding plugin snow (Snow)
Adding plugin wallpaper (Wallpaper)
Adding plugin 3d (3D Windows)
Adding plugin blur (Blur Windows)
Adding plugin rotate (Rotate Cube)
Adding plugin resizeinfo (Resize Info)
Adding plugin trailfocus (Trailfocus)
Adding plugin cubereflex (Cube Reflection)
Adding plugin wall (Desktop Wall)
Adding plugin put (Put)
Adding plugin fadedesktop (Fade to Desktop)
Adding plugin widget (Widget plugin)
Adding plugin imgjpeg (JPEG)
Adding plugin colorfilter (Color filter)
Adding plugin atlantis (Cube Atlantis)
Adding plugin animation (Animations)
Adding plugin cube (Desktop Cube)
Adding plugin firepaint (Paint fire on the screen)
Adding plugin bench (Benchmark)
Adding plugin fakeargb (Color Opacity)
Adding plugin fade (Fading Windows)
Adding plugin ring (Ring Switcher)
Adding plugin workarounds (Workarounds)
Adding core settings (General Options)
Adding plugin dbus (Dbus)
Adding plugin winrules (Window Rules)
Adding plugin mblur (Motion blur)
Adding plugin wobbly (Wobbly Windows)
Adding plugin switcher (Application Switcher)
Adding plugin mousegestures (Mousegestures)
Adding plugin regex (Regex Matching)
Adding plugin water (Water Effect)
Adding plugin keybinding (Gnome keybindings)
Adding plugin crashhandler (Crash handler)
Adding plugin kiosk (Kiosk mode)
Adding plugin visualevent (Visual Event)
Adding plugin cheatsheet (Cheatsheet)
Adding plugin scale (Scale)
Adding plugin cubecaps (Cube Caps)
Adding plugin opacify (Opacify)
Adding plugin expo (Expo)
Adding plugin screenshot (Screenshot)
Adding plugin flash (Flash - An electric storm in your display)
Adding plugin plane (Desktop Plane)
Adding plugin inotify (Inotify)
Adding plugin place (Place Windows)
Adding plugin gears (Cube Gears)
Adding plugin scaleaddon (Scale Addons)
Adding plugin minimize (Minimize Effect)
Adding plugin png (Png)
Adding plugin gotovp (Goto Viewport)
Adding plugin video (Video Playback)
Adding plugin screensaver (Screen Saver)
Adding plugin svg (Svg)
Adding plugin move (Move Window)
Adding plugin glib (GLib)
Adding plugin ezoom (Enhanced Zoom Desktop)
Adding plugin tile (Tile)
Adding plugin clone (Clone Output)
Adding plugin snap (Snapping Windows)
Adding plugin group (Group and Tab Windows)
Adding plugin annotate (Annotate)
Adding plugin vpswitch (Viewport mouse switch)
Adding plugin decoration (Window Decoration)
Adding plugin notification (Uses libnotify to display errors)
Adding plugin quickchange (Allows you to quickly change compiz settings with shortcuts)
Adding plugin resize (Resize Window)
Adding plugin zoom (Zoom Desktop)
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 84, in __init__
    self.ResetMainWidgets()
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 178, in ResetMainWidgets
    self.BuildTable(pluginsVPort)
  File "/usr/local/lib/python2.5/site-packages/ccm/Window.py", line 230, in BuildTable
    pluginEnable.set_sensitive(self.Context.AutoSort)
AttributeError: 'compizconfig.Context' object has no attribute 'AutoSort'
```

I have reinstalled everything several times but it still doesn't work. How can I fix it? I have searched in this forum and the compiz fusion forum as well but didn't find a solution.
Thanks in advance.

Edit: I'm using Feisty + Compiz Fusion from Treviño's repo + nvidia geforce 7300gs

---

### Post by Syirrus on 2007-08-11
I'm having the very same issue :(

---

### Post by era506 on 2007-08-12
At least I'm not the only one with this problem. I'm planing to re-install ubuntu and then install compiz, just to see if it works... maybe tomorrow.

---

### Post by petit.padavoine on 2007-08-12
Try another repo, like the tuxfamily.org one.

You **could** also configure it using gconf-editor, but that's really a hassle :D.

---

### Post by era506 on 2007-08-12
Isn't the Treviños repo at tuxfamily.org?

I have tried to configure it using gconf-editor but all I could do is to change the shortcuts keys, I didn't find a way to activate a plugin or to deactivate an other.

---

### Post by Azzco on 2007-08-13
What could this be...Got the exact same problem but I've had it working before though... I better stop fixing what's working...

---

### Post by era506 on 2007-08-13
> **Azzco said:**
> What could this be...Got the exact same problem but I've had it working before though... I better stop fixing what's working... 

I don't get what you're saying! :confused:

PS: English is not my first lenguage.

---

### Post by mjta on 2007-08-13
Nevermind i'm stupid.

---

### Post by era506 on 2007-08-14
Well, I haven't find a solution anywhere else, so I'll probably do a fresh install tonight.

---

### Post by joshuachad on 2007-08-14
I would try using a flat file backend. Also I concure with what someone else said and use the repos at tuxfamily. They are newer and less buggy in my opinion. Also you could give a shot at installing 0.5.2. It came out a few days ago.

---

### Post by era506 on 2007-08-14
> **joshuachad said:**
> I would try using a flat file backend. Also I concure with what someone else said and use the repos at tuxfamily. They are newer and less buggy in my opinion. Also you could give a shot at installing 0.5.2. It came out a few days ago.

I was thinking about using a flat file too. I'm confused about the tuxfamily repos, I'm currently using treviño's repo which is at tuxfamily.org, are there other repos at that site? Can you give them to me? Is the 0.5.2 at that repo?

---

### Post by joshc on 2007-08-15
OK, I have an extremely hacky way of handling this error. 

I don't do any programming in Python, so I am not able to tell how far reaching this fix is. 
I have been using it and have no problems with compiz-fusion configuration starting anymore. 

It seems that the error is a missing attribute in the binary compizconfig.so

Open /usr/lib/python2.5/site-packages/Windows.py and comment out the line that requests 'AutoSort'. I found it on line 230. 

Open /usr/lib/python2.5/site-packages/Pages.py and comment out the same line. I found it on line 454. 

Once those were commented out, I was able to start just fine. 

Good luck!

---

### Post by era506 on 2007-08-15
Thank you so much for giving me a possible solution joshc!! I'll try it tonight.

---

### Post by realvz on 2007-08-16
> **joshc said:**
> OK, I have an extremely hacky way of handling this error. 

I don't do any programming in Python, so I am not able to tell how far reaching this fix is. 
I have been using it and have no problems with compiz-fusion configuration starting anymore. 

It seems that the error is a missing attribute in the binary compizconfig.so

Open /usr/lib/python2.5/site-packages/Windows.py and comment out the line that requests 'AutoSort'. I found it on line 230. 

Open /usr/lib/python2.5/site-packages/Pages.py and comment out the same line. I found it on line 454. 

Once those were commented out, I was able to start just fine. 

Good luck!

tried this....CCSM does open up :)

but after that when you click on to futher options...nothing happens...and options loose their icons...so just text appears

---

### Post by sympatico on 2007-08-16
i used MC (midnight commander), find all files named *ccsm* and delete it

reinstalled compiz manager (or all compiz fusion deb's).  

works for me.

---

### Post by realvz on 2007-08-16
> **sympatico said:**
> i used MC (midnight commander), find all files named *ccsm* and delete it

reinstalled compiz manager (or all compiz fusion deb's).  

works for me.

can you please tell the locations of the file you found...

---

### Post by sympatico on 2007-08-16
> /usr/share/ccsm

/usr/bin/ccsm

/usr/lib/python2.5/site-packages/ccsm-*


this is most importend files, when i remove this files and reinstall compiz ccsm works good, remove it. and reinstall compiz or compiz manager.

---

### Post by AlexenderReez on 2007-08-16
> **era506 said:**
> I was thinking about using a flat file too. I'm confused about the tuxfamily repos, I'm currently using treviño's repo which is at tuxfamily.org, are there other repos at that site? Can you give them to me? Is the 0.5.2 at that repo?

use at your own risk :)

> [http://shame.tuxfamily.org/repo/](http://shame.tuxfamily.org/repo/)

---

### Post by realvz on 2007-08-16
> **sympatico said:**
> this is most importend files, when i remove this files and reinstall compiz ccsm works good, remove it. and reinstall compiz or compiz manager.

tried deleting these files n reinstalling coompiz + manager....still no ccsm

---

### Post by sympatico on 2007-08-16
remove compiz with purge option, then remove this files, and install compiz (all deb's)

---

### Post by realvz on 2007-08-16
when u purge all these files r already deleted...ccsm still doesnt work

---

### Post by jokester on 2007-08-16
I also have this problem, and ccsm files are removed when compiz packages are purged.

---

### Post by jokester on 2007-08-16
I tried this : 
- uninstall compiz completly
- open your ~/ directory, and delete the .beryl, .compiz, .emerald and other config files which are related to compiz
- reinstall compiz from trevino's debs

Edit : on my computer compiz runs better with that, but ccsm is already down.

---

### Post by stebe on 2007-08-16
I had this problem when upgrading to Compiz Fusion from Beryl.  I believe it is a mismatch between the Ubuntu python and what Compiz is expecting.

A quick fix is to open a terminal and type:
```
sudo gedit /usr/local/lib/python2.5/site-packages/ccm/Window.py
```

Then go down to line #230 which should look like:
```
					pluginEnable.set_sensitive(self.Context.AutoSort)
```

You can comment it out by adding a "#" to it:
```
					#pluginEnable.set_sensitive(self.Context.AutoSort)
```

This makes CCSM run just fine.  Eventually I assume this problem will sort itself out in the packages.

As a note, make sure not to change the indentation of the code as python is funny about that sort of thing.

Good Day,
--Steven

---

### Post by realvz on 2007-08-16
> **stebe said:**
> I had this problem when upgrading to Compiz Fusion from Beryl.  I believe it is a mismatch between the Ubuntu python and what Compiz is expecting.

A quick fix is to open a terminal and type:
```
sudo gedit /usr/local/lib/python2.5/site-packages/ccm/Window.py
```

Then go down to line #230 which should look like:
```
					pluginEnable.set_sensitive(self.Context.AutoSort)
```

You can comment it out by adding a "#" to it:
```
					#pluginEnable.set_sensitive(self.Context.AutoSort)
```

This makes CCSM run just fine.  Eventually I assume this problem will sort itself out in the packages.

As a note, make sure not to change the indentation of the code as python is funny about that sort of thing.

Good Day,
--Steven

OK 3rd time in the day....this does not fix anything...it will just let you open CCSM....but after that you cant navigate to any sub options....

There has to be a fix for this.....

If anyone of you who has a compiz forum ID...can you log a bug...i tried signing up there but they dont seem to be sending me signup confirmation email and so i cant do anythig there.

---

### Post by realvz on 2007-08-16
alright i got it

here are the steps/

 sudo gedit /usr/local/lib/python2.5/site-packages/ccm/Window.py
goto line 230 and add a "#" (without quotes) in front of the line
then
 sudo gedit /usr/local/lib/python2.5/site-packages/ccm/Pages.py
goto line 468 and add a "#" (without quotes) in front of the line



let me know how this one works for you. but as far as i know this problem is now resolved with the above mentioned fix

---

### Post by jokester on 2007-08-17
I tried it at the office, it's perfect : Thank you !
I'm going to post your solution on ubuntu-fr forums.

Regards,
Jk.

---

### Post by Solvax on 2007-08-17
yip

that was a perfect solution...
A lot of people have been looking for this.
Thanks!

Greetz

!Solvax!

---

### Post by era506 on 2007-08-19
> **realvz said:**
> alright i got it

here are the steps/

 sudo gedit /usr/local/lib/python2.5/site-packages/ccm/Window.py
goto line 230 and add a "#" (without quotes) in front of the line
then
 sudo gedit /usr/local/lib/python2.5/site-packages/ccm/Pages.py
goto line 468 and add a "#" (without quotes) in front of the line



let me know how this one works for you. but as far as i know this problem is now resolved with the above mentioned fix

I finally got it!! Thanks!!!
I still noticed something, there are no icons at the ccsm, just white boxes with red x's inside.

PS: By the way, it is line 454 instead of 468 at Pages.py, someone mentioned it in this same thread, that's how I found the error.

---

