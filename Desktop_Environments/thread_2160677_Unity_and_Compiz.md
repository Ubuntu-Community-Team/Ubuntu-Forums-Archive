---
title: "Unity and Compiz"
date: 2013-07-07
forum: Desktop Environments
---

### Post by morick on 2013-07-07
Unity will not run for me in Ubuntu 12.04. Whenever I login I can't get Unity running or the top panel, all that I get is my wallpaper. I've tried completely removing Unity and Compiz via Synaptic and then reinstalling. I've checked off Ubunu Unity Plugin in CCSM but every time I try to run Unity I get this output:

[COLOR=#000000][FONT=Arial]pj@R835:~$ unity[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]unity-panel-service: no process found[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Checking if settings need to be migrated ...no[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Checking if internal files need to be migrated ...no[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Backend     : gconf[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Integration : true[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Profile     : unity[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Adding plugins[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing core options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing composite options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing opengl options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing decor options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing resize options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing scale options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing mousepoll options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing move options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]compiz (expo) - Warn: failed to bind image to texture[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Initializing expo options...done[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]compiz (core) - Error: Couldn't load plugin '/usr/lib/compiz/libunityshell.so' : /usr/lib/compiz/libunityshell.so: undefined symbol: _ZN10CompOption7setNameEPKcNS_4TypeE[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]compiz (core) - Error: Couldn't load plugin 'unityshell'


I've never run into an obstacle like this with Ubuntu since I installed 12.04 when it first released and I REALLY REALLY don't want to reinstall 12.04. Any and all help would be greatly appreciated.[/FONT][/COLOR]

---

### Post by grahammechanical on 2013-07-07
In later versions of Ubuntu we get a warning when we run CCSM that it is possible for us to break the desktop with some of the settings that we change. In later versions we just cannot disable the Unity plugin at all. So, many people did that and broke the desktop that now we cannot do it at all in CCSM.


You might want to install Ubuntu 2D. That should be still avaiable in 12.04 and then you will get to a working disktop where you can use CCSM to set things to their default values. This issue may have been aused by changing some of the settings in CCSM.

Regards.

---

### Post by morick on 2013-07-07
I can get into CCSM and I've changed everything in it to default, however, I still have that libunityshell.so error. I've attached a screenshot of my desktop and on the left-hand side there is a blank space where the Unity launcher used to be but it's gone now. Dash is working fine as you can see but the launcher just doesn't want to load properly because of Compiz which isn't doing the window compositing. I've tried enabling Metacity as a window compositor but that didn't do anything. Unity 2D has the same problem; no Unity launcher.

---

### Post by morick on 2013-07-08
SOLVED

Compiz 0.9.7.12-0ubuntu2 was breaking Unity 5.18.0-0ubuntu2.2~really~ubuntu1+garhuy1. I ended up downgrading (and pinning so this doesn't happen again) to Compiz 0.9.7.12-0ubuntu1.

---

