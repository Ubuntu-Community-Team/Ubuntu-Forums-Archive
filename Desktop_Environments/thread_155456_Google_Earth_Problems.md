---
title: "Google Earth Problems"
date: 2006-04-05
forum: Desktop Environments
---

### Post by nalmeth on 2006-04-05
I like this apps, its fun to play around with and free for the least features, but Google's linux support of course comes up way short.
I'm following [this guide]("https://wiki.ubuntu.com/GoogleEarth?highlight=%28google%29%7C%28earth%29") to installing it in Breezy but no matter what I do I keep getting the error in the screenshots when loading it with:
```
WINEDLLOVERRIDES="ole32,usp10,msvcrt=n" wine PATH_TO_GOOGLEEARTH[/GoogleEarth]("https://wiki.ubuntu.com/GoogleEarth/GoogleEarth").exe
``` I have gotten the psapi.dll and put it in /drive_c/windows/system32 and the dcom98.dll of course. I also grabbed the msvcrt.dll and put it both in system32 and in the google earth folder. 
Not mentioned in the howto, is that you have to change the name to lower-case for it to be used.
```
mv MSVCRT.DLL msvcrt.dll
``` Can anyone direct me where to go from here? Do I really change my color to full 32 bit? I think I'm only on 24 right now. Can you tweak wine to get past this?
BTW, googlearth1.png is what first shows up, I have to hit escape to close the window. I guess those directions (alt-F4) to close it are for windows?

---

### Post by nalmeth on 2006-04-05
Forgot, here's the screenshots.
Please post anything you might know.
thanks

---

