---
title: "American Army Woes in Loading"
date: 2006-07-24
forum: Gaming &amp; Leisure
---

### Post by Scunizi on 2006-07-24
I've looked at tons of threads and feel like I'm going blind trying to load American Army.  I finally got it installed to a point that "Other" off the Applications menu has AA listed.  When I click on it I get the initial splash screen, harddrive light blinks at me and then .... nothing ... the splash screen goes away and that's it.  I've tried to load AA from the Terminal without success from the home directory and from the installed directory which lists the startup file "armyops".  But when I type it in it says "bash: armyops: command not found". So it's tough giving any diagnostic info to go on.  I'm running a nVidia BFG 6600 GT OC with the latest Synapic drivers.  Glsgears runs fine.  Any help would be appriciated.

Edit:  Something weird happened on my install.  I suddenly couldn't boot into Ubuntu so I booted into "rescue" mode and the system buzzed and wurred and logged me me in as root.  After a reboot everything worked peachy keen, nvidia drivers and AA.  I still haven't figured out what happened but I'm happy it's all working..

---

### Post by abowman on 2006-07-25
Where did you download it from?  
I'd get it form here:
[http://0day.icculus.org/armyops/](http://0day.icculus.org/armyops/)
and use md5sum to check the integrity of the file.
Did you install it as root using sudo?

Also, do a search for armyops to figure out where that is:
```

slocate armyops

```
If nothing shows up you might have to run updatedb first.
```

sudo updatedb

```
Then cd to that directory and launch it from there.
```

./armyops

```
Then you should be able to get some error messages when it crashes.

---

### Post by Scunizi on 2006-07-25
Just saw your post after editing mine.  Yep did the download from the site you mentioned.  See my edit.   All working good now.  Thanks!

---

