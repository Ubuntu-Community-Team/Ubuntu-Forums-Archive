---
title: "xcompmgr - how get rid of shadow under top panel"
date: 2005-04-24
forum: Desktop Environments
---

### Post by Humboldt on 2005-04-24
Hi!
I use Gnome and I have installed xcompmgr and I have doneall the tweakings in X11 conf. I use the setting xcompmgr -c -r 3 -l -3 -t -3 to get nice shadows. My only problem now is that there is shadows under the top panel, and that is not quite nice. First there where shadows behind the bottom panel to, but they disapered due to the settings abov. So. How can I get rid of the shadows under the top panel?
Thanks beforehand for any help.

---

### Post by didit on 2005-04-24
just add -C 

xcompmgr -c -C -r 3 -l -3 -t -3 

then you will get rid of shadow on top panel.

-dyt

---

### Post by Humboldt on 2005-04-25
yhea!
It worked. 
But I had to put the big -C first, ie in front of the small -c, to get it working. 
Thanks for help.

---

