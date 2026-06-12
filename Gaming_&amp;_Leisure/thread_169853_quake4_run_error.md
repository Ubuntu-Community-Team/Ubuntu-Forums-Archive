---
title: "quake4 run error"
date: 2006-05-03
forum: Gaming &amp; Leisure
---

### Post by tukster on 2006-05-03
hello
i've just installed quake4 demo
when i run
sh quake4-smp
which is in my home/username/
i get this error:

> ERROR: Couldn't load default.cfg  -  Check your working folder.
********************
Unknown command 'vid_restart'
--------------- BSE Shutdown ----------------
---------------------------------------------
WARNING: rvServerScanGUI::Clear() - invalid scanGUI

idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg  -  Check your working folder.


i've installed as user, the game is in my home/username/quake4
dunno what to do pls help.

---

### Post by sYs^ on 2006-05-03
Is there a directory named /home/username/.quake4 ?

---

### Post by tukster on 2006-05-04
no there isn't one.
sorry for not replaying sonner.

---

### Post by crane on 2006-05-04
Maybe try creating the file .quake4 in you home directory.
Not familiar with user installs but can you not just type quake4 in console to launch it?

---

### Post by deathbyswiftwind on 2006-05-04
the first time i run quake after an install 

quake4 +set s_driver oss

that fixes the sound issue plus creates the ./quake4 in my home after that i just  run quake4 in a console using quake4 and its good to go

---

### Post by tukster on 2006-05-05
hi all
i have reinstalled as superuser.
still no .quake4 dir in my home.
now i can run quake4 but it fails with the error i mentioned above. it still cannot find default.cfg

game is installed in usr/local/games
bins are in ust/local/bin, this is the default setup.
running quake4 +set s_driver oss, fails with the same error.
dunno what to do.

---

### Post by snipe122 on 2006-05-06
have you changed the default color depth in the xorg.conf from 16 to 24 bits?

and why do you run quake4-smp? isnt the executable named quake4?

greets
snipe

---

### Post by tukster on 2006-05-06
from xorg.conf:
DefaultDepth	24

and i ran "quake4", not "quake4-smp" :confused:

---

### Post by snipe122 on 2006-05-06
cause you wrote:

> hello
i've just installed quake4 demo
when i run
sh quake4-smp
which is in my home/username/
i get this error:

strange, both quake4 demo and quake4 work on my comp like a charme...

have you tried installing as root? (just for testing)

---

### Post by tukster on 2006-05-06
yep i've installed it as root

---

### Post by R3linquish3r on 2006-05-07
quake4-smp is for "symetric muti processing" or in lamen terms, running it divided between dual processors.

Sorry but I'm not real versed with Quake 4 :/ In my opinion the game sucks compared to 3 Arena. If ya ever have a problem with that give me a PM cause I've had pretty much everyp problem imaginable ;)

---

