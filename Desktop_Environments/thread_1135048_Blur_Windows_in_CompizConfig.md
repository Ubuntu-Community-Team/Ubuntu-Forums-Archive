---
title: "Blur Windows in CompizConfig"
date: 2009-04-24
forum: Desktop Environments
---

### Post by Mapusaurus on 2009-04-24
I'm on 9.04 and mistakenly enabled Blur Windows in CompizConfig Settings Manager. Now, if I use the mouse/click on anything a big piece of blackness spreads across the screen, obscuring everything. 

So, I need to undo this at the command line. Or, even better, turn off desktop effects, but again I'm going to have to do this at the Bash prompt. Can anyone tell me how to do this? :confused:

---

### Post by free-radical on 2009-04-24
Hello,

go to a text console (ctrl+alt+f1; you know...), log in and edit ~/.gconf/apps/compiz/general/allscreens/options/%gconf.xml. here you should find all activated plugins, so you can remove some lines and restart the X server.

hope that helps.

---

### Post by Mapusaurus on 2009-04-24
Never mind, but thanks for the help anyway! 

I managed to log on as a different user and at the Login screen selected Safe Gnome and was then able to reset everything through the GUI. I've turned off Desktop effects and now there are no problems. 

Desktop Effects in 9.04 don't seem to work with my Intel Graphics card; but then, they didn't work very well in 8.10! Can't say I really miss desktop effects though -seems like more trouble than it's worth- and apart from that I'm very happy with Ubuntu.

---

### Post by lambdacore on 2009-09-13
i had the same problem to a larger extent.
i activated blur to test it and the screen just went black and i couldn't do anything.

i did what free radical said and deleted the lines about "blur" with vi in the conf file.

now everything works great.

thanks!

---

