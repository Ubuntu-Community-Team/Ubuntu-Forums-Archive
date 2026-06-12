---
title: "screenlets compiz and show desktop"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by vapore0n on 2007-08-24
So I have screenlets 0.10 running on gutsy. 

Screenlets set options are: Treat as Widget, Stick to Desktop.
Compiz widget options are: Enabled, Brightness 100%


So the screenlets work and dont disapear when I Show Desktop.
Only problem is that when I reboot I have to press the F9 button for Compiz to show the widget layer. Once I do that the screenlets will stay on the desktop with no problems.

Anyway to emulate a keypress at boot up, or to set them up properly so when I boot up the screenlets show and when I press "Show Desktop" they remain on?

I tried all suggestions I found while goggling. Disabling the "Skip Taskbar" only makes the widget show up on the task bar.

The python virtkey library is supposed to emulate key presses, but there is no documentation at all on how to use i.

---

### Post by Inxsible on 2007-08-24
Wouldn't simply disabling the widget plugin in Compiz Fusion get what you want ?

And Stick to desktop means that the screenlet will be available on all sides of the cube. Else it will only be on the one that you created it on.

---

### Post by vapore0n on 2007-08-24
> **Inxsible said:**
> Wouldn't simply disabling the widget plugin in Compiz Fusion get what you want ?

And Stick to desktop means that the screenlet will be available on all sides of the cube. Else it will only be on the one that you created it on.
diabling the widget pluging will make the screenlets hide when I do "show desktop"


So now im trying to figure how to start with the widget layer turned on. That way the widgets show up at boot.

---

### Post by crazyhunk on 2007-08-24
uncheck  the widget plugin and then go to general options and uncheck
'Hide skip taskbar windows'

now if u do the 'Show Desktop' the widgets dont hide.... :)

---

### Post by vapore0n on 2007-08-25
unchecking "Hide skip taskbar windows" would cause the widgets to show up in the task bar too. And I would still have the problem with show desktop.

Version 0.10 is acting kinda screwy on gutsy. But at least they are stable atm.


Weather widget takes 16MB memory!!

---

### Post by Inxsible on 2007-08-25
yeah, earlier everything ran under screenletsd and so my python process would be around 10 mb for about 4 screenlets...then over time, it would shoot to 300-400 MB ram and i had to kill the screenlets daemon and restart it.

There was a memory leak somewhere. Now, though each screenlet has its own python process and they each take about 10 mb ..havent let them run for long so dont know if the memory leak still exists.

---

### Post by fuoco on 2007-08-31
How do I use the widget plugin, and set it so it works like in os x dashboard? right now i can't get the widgets to connect to the plugin's mode, they just show up all the time.

---

### Post by vapore0n on 2007-08-31
> **fuoco said:**
> How do I use the widget plugin, and set it so it works like in os x dashboard? right now i can't get the widgets to connect to the plugin's mode, they just show up all the time.
how they work on my computer is, you set the plugin on, set the screenlet to act as a widget, and press F9 to make them show/disapear

If you set brightness up to 100% and remove "disable on click"  you can leave them up and still use the desktop. Sort of making them permanent. But it doesnt work 100%. On bootup the screenlets settings seem to get reset and the show above windwows and I have to set them back to stay below.


So im back to trying to find a way to have permanent screenlets on the desktop.

---

### Post by fuoco on 2007-08-31
> **vapore0n said:**
> how they work on my computer is, you set the plugin on, set the screenlet to act as a widget, and press F9 to make them show/disapear

If you set brightness up to 100% and remove "disable on click"  you can leave them up and still use the desktop. Sort of making them permanent. But it doesnt work 100%. On bootup the screenlets settings seem to get reset and the show above windwows and I have to set them back to stay below.


So im back to trying to find a way to have permanent screenlets on the desktop.

any idea why for me it keeps staying on the desktop no matter if i activate or deactivate widget mode? (I see the widget layer because of it's brightness but it doesn't do anything with the screenlets widgets...

---

### Post by Inxsible on 2007-08-31
> **fuoco said:**
> any idea why for me it keeps staying on the desktop no matter if i activate or deactivate widget mode? (I see the widget layer because of it's brightness but it doesn't do anything with the screenlets widgets...
Right click on each screenlet and select Widget, also maybe uncheck Sticky or any other options you have selected.

---

### Post by fuoco on 2007-08-31
> **Inxsible said:**
> Right click on each screenlet and select Widget, also maybe uncheck Sticky or any other options you have selected.

Yes I did that of course, i left only Widget on, and tried both with and without Sticky, and it doesn't change anything. the screenlet stays visible on the desktop, or over applications like any normal app

---

### Post by cwgannon on 2007-11-27
I suppose this depends on your setup and what you run, but you can achieve the functionality you're looking for by unchecking Hide Skip Taskbar Windows in CCSM's General Options and appending name=Screenlet.py$ to the end of your list of windows that should skip the taskbar (xxx | name=Screenlet.py$) in CCSM's Window Rules plugin.  (If this fails, be sure to enable theRegex Matching plugin.)

Unfortunately, if there are any other windows up on your desktop that aren't in the taskbar, they, too, will not be hidden by your show desktop command, but really, I'm not sure how many of said windows you'll really have to deal with.

If this doesn't work, futz around with the Show Desktop command.  There's a section which controls which windows are affected, so maybe a !name=Screenlet.py$ would be useful in some context.  From what I have found though, the General Options setting I referred to earlier that Hides Skip Taskbar Windows seems to override these options, which really defeats the purpose of what we're trying to do.

Anyway, good luck.

---

### Post by brunods on 2008-01-16
> **vapore0n said:**
> how they work on my computer is, you set the plugin on, set the screenlet to act as a widget, and press F9 to make them show/disapear

If you set brightness up to 100% and remove "disable on click"  you can leave them up and still use the desktop. Sort of making them permanent. But it doesnt work 100%. On bootup the screenlets settings seem to get reset and the show above windwows and I have to set them back to stay below.


So im back to trying to find a way to have permanent screenlets on the desktop.
The best idea to do that is the following:
I've been having the same problem that some of the widgets would come back above other windows.
The easiest way to make 'em all very obedient is using another compiz plugin.
-First you should set all your screenlets to the Widget layer:
enter the options of the Widget plugin and insert "class=Screenlet" in the textbox to say all screenlets shall be widgets!
-Then enable the plugin called "Window Rules", and insert the same text "class=Screenlet" in the textbox called "Below".

It worked smooth for me. I tried to have the widgets never "minimize" with the window rules plugin, but it just won't work.

Wish you luck.

---

### Post by cartisdm on 2008-04-27
I hate to revive and old thread but hopefully it will get noticed by someone.  I can't seem to get my widgets to appear on my other desktops after a reboot.  I have the "sticky" option checked and if I uncheck it, then recheck it they appear on the other desktops.  But as soon as I reboot they only appear on my first desktop.  then I have to uncheck and recheck them again.

I also have "lock" "widget" "keep below" selected in addition to "sticky"

---

### Post by Hells_Dark on 2008-05-08
> **cartisdm said:**
>  But as soon as I reboot they only appear on my first desktop.  then I have to uncheck and recheck them again.

I also have "lock" "widget" "keep below" selected in addition to "sticky"

Same problem here.

---

### Post by cartisdm on 2008-05-08
> **Hells_Dark said:**
> Same problem here.

Check out some of the solutions on this other thread.  I haven't had a chance to really sit down and try them out because I've been too busy but they're worth giving a shot.

[The Other Thread]("http://ubuntuforums.org/showthread.php?t=773738&goto=newpost")

---

### Post by MiniMe on 2008-06-27
If you are using gconf then start gconf-editor and uncheck this value:

/apps/compiz/general/allscreens/options/hide_skip_taskbar_windows

No need to set "Treat as widget" in the screenlet and no need to enable "Widget Layer" in compizConfig. Screenlets will no longer be minimized along with other windows. Worked like a charm for me anyway. 

Got it from this post: [http://forum.compiz-fusion.org/showthread.php?t=323&page=83](http://forum.compiz-fusion.org/showthread.php?t=323&page=83)

---

### Post by Sonic Reducer on 2008-07-07
i know this is an old thread, but i'm having the same problem on my desktop. i've done the same steps on my laptop and it's worked fine, but my sysmonitor screenlet keeps minimizing.

[[IMG]http://img114.imageshack.us/img114/8243/screenletsrc0.th.png[/IMG]](http://img114.imageshack.us/my.php?image=screenletsrc0.png)

i'm using the sysmonitor screenlet v0.1 with screenlets 0.1.2

---

### Post by MiniMe on 2008-07-09
Hi Sonic. Make sure you don't run gconf-editor with sudo or the settings won't be changed for your user. Run gconf-editor under the user that you want the settings applied. Sorry if you already know this but I thought I'd point it out just in case.

---

### Post by Sonic Reducer on 2008-07-10
> **MiniMe said:**
> Hi Sonic. Make sure you don't run gconf-editor with sudo or the settings won't be changed for your user. Run gconf-editor under the user that you want the settings applied. Sorry if you already know this but I thought I'd point it out just in case.

actually, youre right in both respects, i know gksu should be used for graphical sudo, but i stil ran it as sudo

---

