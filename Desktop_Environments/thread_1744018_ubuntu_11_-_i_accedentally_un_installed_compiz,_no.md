---
title: "ubuntu 11 - i accedentally un installed compiz, now my desktop is fragged"
date: 2011-04-30
forum: Desktop Environments
---

### Post by ib4ngsh33p on 2011-04-30
i removed compiz because the effects it had in 10 did not work in 11, but it turns out, that was BAD. now i have no window borders, the launch bar on the left, or and icons. trying to relaunch compiz i get the following:
```
matthew@matthew-laptop:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Initializing mousepoll options...done
Initializing move options...done
Initializing place options...done
Initializing resize options...done
Initializing gnomecompat options...done
Initializing vpswitch options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

Initializing snap options...done
Initializing session options...done
compiz (core) - Error: Plugin 'opengl' not loaded.

Initializing grid options...done
Setting Update "run_command_terminal_key"
```PLEASE help asap. i need my laptop for school tomorrow, and i cannot afford to wipe it and loose my files 10hrs before class

---

### Post by manzdagratiano on 2011-04-30
It seems to me that you have not really uninstalled compiz, else it would have complained that it cannot find 'compiz'. Nevertheless, if you have, reinstall it, and what you also need to do however, is to install 'ccsm' from the repositories:

```
sudo apt-get install compiz ccsm
```

Then, go to System -> Preferences -> Compiz Config Settings Manager, and enable the OpenGL plugins. Hopefully this will solve your issues.

---

### Post by ib4ngsh33p on 2011-04-30
i did that, and so far, that has worked, but it seems a little unstable ( screen tearing, and slow boot/reboot ) but i assume this might be more weighed towards a new release not towards my stupidity. 

but thank you for all your help!!

---

### Post by GameDog(A) on 2011-04-30
I had the same exact problem. I had to go to CCSM and rechecked my Compiz options and even with that I didn't get back my toolbar or my maximize,minimize, close options back. Just got rid of the black Blocs on my desktop. So I uninstalled 11.04. And log on under "Classic ?(forgot name of option)".
 I think I'll wait a month or two to let the bugs get rolled out.
And the OS does load a bit slower too

---

### Post by manzdagratiano on 2011-04-30
Did you enable the "Resize window", "Minimize window" etc options under "Window Decorations"? That could be the only thing wrong. Compiz has not really given me a problem since the first crash.

---

