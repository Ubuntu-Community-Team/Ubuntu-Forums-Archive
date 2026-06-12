---
title: "counter strike - freeze"
date: 2007-10-17
forum: Gaming &amp; Leisure
---

### Post by usarmykr on 2007-10-17
Can't seem to find a fix online.  I am running kubuntu 7.10, wine 0.9.47.  Steam and all installed perfect.  CSS works, sound works.  I get into the game and about 10 seconds in, time enough to buy a gun and run 2 steps, it freezes.  Dosent exaclt crash, sound lags and screen stops, so I force quit.  Don;t know how to run it from the console and get errors, but heres my shortcut is it matters 

cd ~/.wine/drive_c/Program\ Files/Steam && WINEDEBUG=-all wine steam -applaunch 240 -width 1440 -height 900 -dxlevel 80

Anyone know how to fix this, or where to find the fix?  

PS - I run wow perfectly, and have heard of some wow patched wine versions, anyone know about that?

---

### Post by berserker on 2007-10-18
Open up a terminal and type in

```
winecfg
```

Go to the "Applications" tab, "Add application" and drill down to the Steam folder and select "Steam.exe".  Choose "Windows XP" as the version of Windows to run.  Then "Add application" again and select "hl2.exe".  Choose "Windows 98" as the version of Windows.  Click OK and then launch the game again.

My CS:S was freezing as well until I did the above.

Steam.exe is located in ~/.wine/drive_c/Program Files/Steam/ on my machine.
hl2.exe is located in ~/.wine/drive_c/Program Files/Steam/steamapps/[user_name]/counter-strike source/

HTH.

---

### Post by usarmykr on 2007-10-18
OK cool, will try once I get home, at work now :X

---

