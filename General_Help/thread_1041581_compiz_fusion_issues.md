---
title: "compiz fusion issues"
date: 2009-01-16
forum: General Help
---

### Post by TudorH56 on 2009-01-16
I have recently installed ubuntu intrepid ibex 8.10 on my acer inspire one, on this i then tried out the compiz config system manager i choose an effect indicated by a "red ball", unfortunately i can't remember which one, this then caused just black spaces to appear instead of windows i managed to run terminal an uninstall compiz and manager. I have tried reinstalling it all as i had some effects which i found useful working however doing so caused the same problem indicating settings have remained, how can install compiz again without the settings already in action set?

---

### Post by Wartender on 2009-01-16
you have to go to synaptic and mark it for complete removal, this will remove configuration files as well, you can disable it from the terminal as well but i'm not sure how.

---

### Post by Wartender on 2009-01-16
wait here we go here's the command
```
key="gconftool-2 /apps/compiz/general/allscreens/options/active_plugins" ; $key -s -t string $($key -g | sed -e 's/,blur//g')
```
this will disable the blur plugin, which is most likely the cause of your problem, if it is the motion blur one then this is the code
```
key="gconftool-2 /apps/compiz/general/allscreens/options/active_plugins" ; $key -s -t string $($key -g | sed -e 's/,mblur//g')
```
it's most likely the blur one though, so try it first (before marking for complete removal, this is better.

---

