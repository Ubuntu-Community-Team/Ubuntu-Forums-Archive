---
title: "Evolution running in system tray?"
date: 2009-01-21
forum: General Help
---

### Post by coiax on 2009-01-21
I'm trying to get the hang of Evolution as my email client for my Ubuntu, but I can't seem to find anything that would allow it to run just as an icon in the system tray, meaning that I don't have to keep the window open for it to check my mail now and again.

Have I missed some options somewhere?

---

### Post by sockrebel on 2009-01-21
it's not in the options anywhere.
but another program (alltray) will do the trick.
```
sudo apt-get install alltray
```
alltray used to have problems when running with compiz, but i'm not sure if that is still the case.

you can either then go to applications->accessories->alltray
 and then click on your evolution window

or you can just change your launcher command to read "alltray -na -s evolution"



> **coiax said:**
> I'm trying to get the hang of Evolution as my email client for my Ubuntu, but I can't seem to find anything that would allow it to run just as an icon in the system tray, meaning that I don't have to keep the window open for it to check my mail now and again.

Have I missed some options somewhere?

---

