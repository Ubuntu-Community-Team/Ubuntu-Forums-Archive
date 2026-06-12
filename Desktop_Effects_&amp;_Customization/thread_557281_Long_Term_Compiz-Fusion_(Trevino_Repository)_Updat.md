---
title: "Long Term Compiz-Fusion (Trevino Repository) Update Info Thread?"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by tak1150 on 2007-09-22
I hope I'm proposing something good... Thanks to the Trevino Repo, we get updates quite frequently. As it really is BLEEDING-EDGE, we sometimes get :D with the update and sometimes :-(.

There have been separate threads about each of the problems that occurred with each update that was problematic. This may be the way to go, but I was thinking "wouldn't it be more convenient if people can just go to one thread and get all the info on the Trevino updates?"

So the format I'm proposing is something like (note: I'm making up the info below):

[SIZE="5"]09/14/07 Update[/SIZE]
[LIST]
[*]fixes previous problems
[*]works great!
[/LIST]

[SIZE="5"]
09/22/07 Update[/SIZE]
[LIST]
[*]when you start Compiz, the laptop jumps (a bug?)
[/LIST]

And only a few people should post to confirm the problem so it doesn't get necessarily long. And if there is a fix, that's great or the more patient ones can report that the next update fixed the problem. 

With enough said, I'm going to try the updates for today (September 22).

---

### Post by tak1150 on 2007-09-22
[SIZE="5"]09/22/07 Update[/SIZE]
As far as I can tell, it is working flawlessly. I haven't notice any changes.

---

### Post by Sammm_ on 2007-09-22
[SIZE="5"]09/22/07 Update[/SIZE] 
[LIST]
[*]Killed it for me.
[/LIST]

[Long Story]
 I updated, all was fine then I realised CCSM wouldn't open so I restarted X, when I logged back in it CF was dead. No window decorations, no cube, nothing.

Trying to run CCSM Produces this error.

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

---

### Post by tak1150 on 2007-09-22
sammm_

that actually happened to me too. But I after I rebooted the computer, it all worked. Restarting the X-server did not do it for me (ie Alt+Ctrl+Backspace)

---

### Post by Sammm_ on 2007-09-22
I reebooted, no luck. :(

---

### Post by petit.padavoine on 2007-09-22
If one update breaks compiz, you can just make do w/o compiz for some time and wait for a fix in the next update(s). After all, it's the development version, intended mostly for developers.

---

### Post by tak1150 on 2007-09-22
> **petit.padavoine said:**
> If one update breaks compiz, you can just make do w/o compiz for some time and wait for a fix in the next update(s). After all, it's the development version, intended mostly for developers.

Sure. So this thread is not intended for people who don't mind not having Compiz for a while.

Now that Sammm_ reported his/her problems here, others can be cautious about getting this particular update for now. I think this thread would really serve the community well.
So thanks to sammm_ for reporting it and for sort of being the sacrifice :)

Review:
If I may ask, on this thread, I'd only like to have:
[LIST]
[*]Reporting of problems w/ particular updates
[*]Reporting of known solutions (I've already kind of violated this
[/LIST]

---

### Post by Chazall1 on 2007-09-22
09/22/07 Update

Having problems with 3d windows? When I enable it and i do the cube the windows disappear (the more windows i have open the farther the cube zooms out), of course when I disable it it works fine with regular 2d windows. It worked fine 3 updates back, after then, it either got worse or stayed the same.

---

### Post by lazd on 2007-09-22
[SIZE="5"]9/22/07 Update[/SIZE]
I have (reluctantly) not been running Compiz-Fusion for the past couple weeks, but after seeing this update, I thought I'd check it out to see if any of the bugs that had been bothering me were fixed. Here's what I found.

[SIZE="2"]**Old Bugs**[/SIZE]
[LIST]
[*]No window borders on secondary monitor (using metacity, nvidia drives via ENVY, 2 Xsessions)
[*]Delay before the popup of menus, windows, ect
[*]Still have to run 'compiz --replace'. In the past, very few applications would actually open and display windows until this was typed (compiz effects worked, but the system wasn't functional). When I tried it after this update, compiz effects would work, but when I start an application compiz would unload and the application would open properly (without compiz, of course).
   +**WORKAROUND:** run 'compiz --replace' every time you start or put it in the "Startup Programs" secton of the "Sessions" preference panel. I have 'metacity --replace' in my "Startup Programs" for now until Compiz is more stable (no need to uninstall completely, I still want to give compiz a chance!)
[/LIST]

[SIZE="2"]**New Bugs**[/SIZE]
[LIST]
[*]Metacity crash when using volume/pause buttons on Microsoft Natural Ergonomic 4000 (not using KeyTouch, just standard 'Keyboard Shortcuts') while running Rhythmbox. I noticed a nice clean volume indicator when I adjusted the volume the first few times, but I hit "Pause" (bound to "Next Track"), all of the sudden my system looked GTK+ for a few seconds until metacity restarted itself. I was about to say I can reproduce this problem consistently, but it seems to only happen the first time I press the "Pause" button and I'm not sure if it has to do with which Xsession has focus when I press this button. The first time I had this problem, the nice clean indicator referenced above was replaced with the standard indicator and using the controls did not result in any crashes. The second time I had this problem, I was able to get it to crash on two separate instances, but when I tried for a 3rd crash, everything just worked with the nice clean indicator and all. 
[*]3D windows caused windows to disappear and showed only 1 desktop when rotated.
    +**WORKAROUND:** disable it, I hate 3D windows anyway as it makes the desktop zoom back in REALLY SLOWLY (is this a bug too? :))
[/LIST]

[SIZE="2"]**Fixed**[/SIZE]
[LIST]
[*]I used to have a problem with the "Show Desktop" plugin making windows unable to move or resize until minimized&restored, but this seems to have been fixed. There have been SEVERAL releases since I first had this problem, so I wouldn't attribute the fix to this version in particular.[/LIST]

Thanks for all the hard work, on both the community and developer sides! It's for the benefit of all if you clearly format your forum postings (use bold, ordered list, size) and double check to make sure the information you're posting is correct, so take the extra time if you actually want to see a result!

---

### Post by Sammm_ on 2007-09-22
[SIZE="5"]General Fix[/SIZE]

This should fix any damage caused by any upgrade.

[QUOTE=http://forum.compiz-fusion.org/showthread.php?t=1012&page=26]I opened nautilus, went into /var/cache/apt/archives, view as list, sort by date, picked the second latest version of the following packages (but not THE latest since its broken) *[SIZE="1"][Pick the files from the last working install][/SIZE]*:

compiz
compizconfig-settings-manager
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-fusion-plugins-unofficial
compiz-fusion-plugins-unsupported
compiz-gnome
compiz-plugins
emerald
libcompizconfig0
libdecoration0
libemeraldengine0
python-compizconfig

I copied the files in a new folder, and then opened a terminal in this new folder, and did a sudo dpkg -i * to downgrade everything to its previous version... update manager is complaining of course, but for now, and until this problem is fixed, i prefer a working compiz than no compiz at all[/QUOTE]

---

### Post by tak1150 on 2007-10-02
[SIZE="4"]09/30/07 Update[/SIZE]

[LIST]
[*]Sorry the date may be off by +-1
[*]Gnome panel fails to show up for the 1st boot, but it appears fine after the 1st login
[/LIST]

---

### Post by bimmerd00d on 2007-10-02
> **tak1150 said:**
> [SIZE="4"]09/30/07 Update[/SIZE]

[LIST]
[*]Sorry the date may be off by +-1
[*]Gnome panel fails to show up for the 1st boot, but it appears fine after the 1st login
[/LIST]

Mine does this as well.  If i click in the area where it would be it appears. :D

---

