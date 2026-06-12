---
title: "Stuck in Unity 2D"
date: 2012-11-04
forum: Desktop Environments
---

### Post by 123user456 on 2012-11-04
Hi,

First, here's some background:

Ubuntu 12.04 64bit, graphics card: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series] (output from lspci | grep VGA)


My whole issue stemmed from trying to give different workspaces different backgrounds.  To this end, I installed compizconfig-settings-manager.

Then I did something stupid, not knowing precisely what compiz or unity is: I first ran the command 'compiz', which gave me some kind of message saying 'try compiz --replace instead.'  So I ran 'compiz --replace,' and that's when the problems started.

Basically, everything works fine, except that my task switcher (alt-tab) is an ugly gray color that shows only the icons and not miniature versions of windows.  Also, when I log in, I get a grey screen for a moment, which later goes away.  My workspace switcher (ctrl-alt-arrow) is also ugly and gray.  I suppose the issues a merely cosmetic, but I cannot figure out how to get the 'pretty' versions back.

I been to a huge amount of threads, blogs, and pages related to this, and nothing I've done seems to resolve the issue.  I've tried unity --reset (seg fault), ccsm (doesn't have any effect).

One thing that seems likely to me is that I am somehow stuck in Unity-2d. I have no idea how to get to 3d.  The graphics driver I'm using (amd / ati fglrx) seems to be installed and activated. 

Does anyone know
1. what is it about compiz --replace that can make everything ugly
2. if I can simply revert my system setting to 24 hrs ago, before the problem started?

Please let me know of any other kinds of information I need to provide.

Thank you.

---

### Post by jonnyboysmithy on 2012-11-04
Sounds to me like you messed up your compiz settings. 
If you look around in compiz settings manager there is a option to reset all settings to default. From memory its under Preferences>Reset to defaults.
I screwed up my compiz similar to you a few times :)

If you want to restart compiz use the compiz --replace command. I would typically use that command compiz when something goes funny (occasionally happens when I apply a setting).
Same thing with unity --replace. I also use that to restart it when something goes funny.

[According to tuxgarage (link):]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html") > If resetting Unity alone is not enough, try resetting the rest of Compiz' settings:
```

gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config

```

---

### Post by 123user456 on 2012-11-04
I've been to the tuxgarage, and followed closely those instructions.  Nothing's helped.   Here's what I get when I do compiz --replace:


 compiz --replace
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2000004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3800031

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1400002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e00006

Initializing composite options...done
Segmentation fault (core dumped)


And here's what I get if I run unity --replace:


unity --replace
unity-panel-service: no process found
Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
compiz (core) - Warn: failed to receive ConfigureNotify event on 0x2000004

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3800031

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1400002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x1600002

compiz (core) - Warn: failed to receive ConfigureNotify event on 0x3e00881

Initializing composite options...done
Segmentation fault (core dumped)

Nothing seems to work.

Also, setting back to default settings in ccsm has no effect, just like anything else I try to do with ccsm - there is no effect whatsoever.

Any way I can just reinstate previous system settings, before I ever installed ccsm?

---

### Post by barnacle51 on 2012-11-04
I have a Dell 1640 with a Readon HD 3650. It will not run in Ubuntu 14.10. Will not even boot. Went back to 1404 and runs fine.

---

