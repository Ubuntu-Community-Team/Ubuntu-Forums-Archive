---
title: "Desktop cube, gnome classic in 11.10"
date: 2011-11-22
forum: Desktop Environments
---

### Post by fleminwr on 2011-11-22
Hi, I just upgraded from 11.10 from 10.10. The unity/launchpad thing isn't my thing so I'm trying to get "gnome classic" to work. However, I cannot get desktop cube to work in gnome classic (it does work in Unity though, albeit with the annoying flicker). 
 
The thing I cannot figure out, is desktop cube even available for gnome classic? Is there some trick necessary to enable it that I'm missing? When I fire up CCSM it just seems like I'm banging buttons, nothing really happens.
 
Thanks.

---

### Post by stinkeye on 2011-11-22
Just replace gnome classic's window manager, metacity with compiz
ie
```
compiz --replace
```
and disable the unity plugin in ccsm.

---

### Post by mikewhatever on 2011-11-22
Gnome Classic runs Metacity as a window manager. You could try switching to Compiz by running 'compiz --replace'. I've no idea it it's going to work though.

---

### Post by jimmydean886-2 on 2011-11-22
That fix does work.

Just add that to your startup applications, and make sure that the Unity plugin isn't active. Here's how to check:

```
sudo apt-get install compizconfig-settings-manager
```

Launch the compiz config settings manager after running this code (which installs it) and uncheck the "ubuntu unity plugin" item if it is checked.

---

### Post by fleminwr on 2011-11-22
That was easy!  Worked like a charm.
 
Thank you very much for the replies.

---

### Post by fleminwr on 2011-11-22
maybe I spoke too soon.
 
How do I get compiz to load automatically each time I log in?
 
Also, when I use the compiz --replace command, the process in the terminal hangs, usually not in the same place.  I get some warning messages, such as:
 
compiz (core) - Warn:  no exact match for ConfigureNotify on 0x3200090!
. . . .
compiz (core) - Warn:  this should never happen.  you should probably file a bug about this.
 
every once in a while I can get compiz to start if I kill the terminal session.  
 
I don't think it's supposed to work this way, any suggestions are appreciated.

---

