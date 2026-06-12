---
title: "Quake III problem"
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by Shrimpen on 2007-03-20
I've installed Quake III Arena on my Ubuntu 6.10 system and it's working great except everytime I start the game, my previous game progress and settings are gone. Anyone know how to fix this?

/Shrimpen

---

### Post by Rumor on 2007-03-20
Do you have a file in your ~/.q3a/baseq3 directory called "games.log"? That's where Q3 stores your progress.

---

### Post by Shrimpen on 2007-03-20
> **Rumor said:**
> Do you have a file in your ~/.q3a/baseq3 directory called "games.log"? That's where Q3 stores your progress.
No actually I dont, do you think I can simply create one and hope it begins to log?

---

### Post by Rumor on 2007-03-20
Well, if there isn't one there, then I doubt it will suddenly start logging. Do you have any files in ~/.q3a? How did you install the game, and have you updated to the latest point release?

---

### Post by zcal on 2007-03-20
Try running Quake III as root.

sudo quake3

Set all of your settings as you like them, then quit the game and then start it again without being root.  My Quake III install set up my .q3a folder as a root-access only, so it'll only keep the config file it generates if I'm playing as root.  Could be yours did the same thing.

---

### Post by dmn_clown on 2007-03-22
> **zcal said:**
> Try running Quake III as root.

sudo quake3

Set all of your settings as you like them, then quit the game and then start it again without being root.  My Quake III install set up my .q3a folder as a root-access only, so it'll only keep the config file it generates if I'm playing as root.  Could be yours did the same thing.

Ever thought about chown -R <username>:<groupname> ~/.q3a and not running a game with root access?  This isn't MS Windows, programs do not and **should not** be run with root access.

---

### Post by Stickymaddness on 2007-03-24
I had this same problem, I fixed it by

```


sudo quake3


```

I think running it once as root generates the settings file(s), since now if I run it normally it keeps all my settings/progress.

---

