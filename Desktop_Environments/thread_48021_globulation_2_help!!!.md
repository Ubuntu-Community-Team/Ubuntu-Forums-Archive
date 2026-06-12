---
title: "globulation 2 help!!!"
date: 2005-07-10
forum: Desktop Environments
---

### Post by zeromod on 2005-07-10
if anyone could help me that would be sweet lol. i had glob2 running by way of typing glob2 into the terminal i went to graphics options and enabled gl and fullscreen now when i try to run glob2 it seg faults and sdl parachutes at 32bb etc. now i beleive the issue may be that its trying to create an 800x600 window at 32bit and having issues however it shouldnt as my nvidia card is configured and i run cedega emu games such as war3 and gta3 vice city at 1024x768 all the time also native neverwinter nights for linux. there are no sdl issues that i know of as other sdl dependant apps work fine. i tried uninstalling glob through apt (synaptic and through terminal) and then reinstalling however it seems to leave the config files after reinstall  so it still tries to go fullscreen etc. i tried passing the glob2 -s640x480 and -r and all kinds of parameters to keep it from trying to load with gl fullscreen but it wont. any help ? lol maybe someone could tell me where the config file is? ive done a whereis and locate but it just shows the basic man directory and the bin. thanks sorry for the long post and if its in the wrong place sorry sorry :)

edit: ok i just entered the parameter glob2 -G to disable gl and its fine at 1024x768 odd as gl is not an issue i get around 3000 fps with my lowend geforcefx5200 128mb. gotta love linux lol i can run neverwinter nights and half life 2 at nearly full specs but need to disable gl to play globs2 lmao. hope this maybe helped someone if they ran into this issue.

---

### Post by Lord Illidan on 2006-01-01
I also had this problem under all distros I ran Globulation on. Open GL wouldn't work.

However, their latest alpha version does work in GL mode, I've tried it. It's much faster, btw. CPU was at below 50% the whole time, in full resolution, while in SDL mode, CPU was constantly at 100%.

Get the deb from here : [http://epfl.ysagoon.com/wiki//index.php?n=Globulation2.Download](http://epfl.ysagoon.com/wiki//index.php?n=Globulation2.Download)

---

