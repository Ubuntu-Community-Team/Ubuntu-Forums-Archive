---
title: "DosBox launcher driving me crazy !"
date: 2011-07-19
forum: Gaming &amp; Leisure
---

### Post by brunobliss on 2011-07-19
Hey guys, i have a **dosbox.cfg** file set with my preferred configurations, i open dosbox (portable version) and it all works well, my configs load.

As soon as i try to make a launcher for the application, no settings load, it's like it has a default .cfg file or none at all.

I used to have dosbox installed and uninstalled it and have deleted every single trace of dosbox related files, still, i can't get the launcher to work with my settings, is this a known problem or what?

---

### Post by Perfect Storm on 2011-07-19
May I suggest using DBGL instead (Dosbox Game Launcher), you can set up each programs/Games with its own settings easily and save all the configurations as backup or taking the configurations to another computer: [http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)


[[img]http://s3.postimage.org/pc2runoq8/Daggerfall_pre.png[/img]](http://postimage.org/image/z7647tj8/)

---

### Post by R33D3M33R on 2011-07-20
You have to set your launcher to use custom config with the switch:

```
-conf "/path/to/your/config/dosbox.cfg"
```

---

### Post by mastablasta on 2011-07-20
DBGL should be in the repos or even default install. :-)

---

### Post by brunobliss on 2011-07-20
thank you for the suggestions guys! I actually use DBGL, but before i create a fancy profile i like to test my games, and i have dozens of games to test, ence the need of a quick access to DOSBOX.

Anyways, i'll try your suggestions out and let you guys know which one worked out the best.

CheerS!

---

### Post by mastablasta on 2011-07-20
stick 'em in a directory with subdirectories for each game. make dos box launcher that automaticly mounts that directory then just move arround in it with DOS commands. you can test plenty of games like that. if you just give them a short try and then continue with a new one...

---

