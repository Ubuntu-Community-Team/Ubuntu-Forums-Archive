---
title: "Gutsy compizconfig question"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by zaomaster on 2007-12-04
I upgraded to gutsy from Feisty and I was using Beryl at the time (which I kept and continued to use until yesterday).  After dumping Beryl because it wouldn't draw borders on a program I run through wine, I went to try and use compiz-fusion.  I have all the packages installed and some of the effects work, but I can't open compizconfig settings manager.  When I click on it the system works as if it's trying to open it, but then nothing happens.  Any help?  Oh, and I had things like the cube working through beryl, but now it's gone back to a wall.  I'm sure that will get fixed if I could open the settings manager, but once you get used to one thing it's hard to go back.

thanks for the help.

---

### Post by ronmarley1 on 2007-12-04
I had the same issue when I upgraded from Feisty.  What fixed it for me was completely removing compizconfig-settings-manager in Synaptic and then reinstalling.  In Gutsy, it then shows up as "Advanced Desktop Effects Settings" on the System -->Preferences menu.  Or, you can run ```
ccsm
``` from a terminal.  If it's still broken after reinstalling, running from a terminal should give some error messages.

EDIT: By the way, I eventually did a fresh install of Gutsy, and things work much better than the upgrade.

---

### Post by zaomaster on 2007-12-05
I keep hearing about this fresh install thing, but I'm rather new to this linux world.  How do you not lose all your information?  Do you have to uninstall Gutsy before the fresh install, or is it simply like the first install and you run it from the livecd and it just overwrites everything?

thanks again.

---

### Post by mozetti on 2007-12-05
If you created a separate partition for your /home directory, then just format the root partition and install gutsy to that partition. During the setup it will present your other partition(s) to you and you can edit how to mount them.

As long as you use the same username, then your home directory and everything saved there (including your config files for the programs) will be in your home directory. You'd just have to re-install your programs.

---

### Post by zaomaster on 2007-12-05
> **ronmarley1 said:**
> I had the same issue when I upgraded from Feisty.  What fixed it for me was completely removing compizconfig-settings-manager in Synaptic and then reinstalling.  In Gutsy, it then shows up as "Advanced Desktop Effects Settings" on the System -->Preferences menu.  Or, you can run ```
ccsm
``` from a terminal.  If it's still broken after reinstalling, running from a terminal should give some error messages.

EDIT: By the way, I eventually did a fresh install of Gutsy, and things work much better than the upgrade.

This is the output of running ccsm in a terminal:

```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
```

what does it mean?

---

### Post by ronmarley1 on 2007-12-05
> **zaomaster said:**
> This is the output of running ccsm in a terminal:

```
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
```

what does it mean?

I'm not entirely sure.  Did you try and uninstall and then reinstall compizconfig-settings-manager before trying to run it in a terminal?

---

### Post by zaomaster on 2007-12-06
yeah, I did... man, I wasn't looking forward to reinstalling gutsy, but I just might have to...

---

### Post by ronmarley1 on 2007-12-06
> **zaomaster said:**
> yeah, I did... man, I wasn't looking forward to reinstalling gutsy, but I just might have to...

At this point, I don't think I can help.  Maybe try the compiz forums at: [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)
Sorry I was not of more assistance.

---

### Post by zaomaster on 2007-12-06
no, you helped.  I was able to get ccsm to work, but...

somehow in the process destroyed my ability to actually have desktop effects.  man, i wish this was easier.

---

### Post by Grishka on 2007-12-06
there's probably no need to reinstall gutsy, I've upgraded from feisty with beryl to gutsy with compiz-fusion with little problem. you ought to try removing beryl and compiz completely from your system (uninstall and completely remove beryl's and compiz's configuration directories), before installing compiz-fusion again. if you're up to it, I would suggest installing from git, as git version seems to fix a lot of problems and adds some new stuff. stick with compiz from ubuntu repos if you're not experienced in compiling stuff under linux.

---

