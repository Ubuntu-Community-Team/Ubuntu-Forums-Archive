---
title: "Setting default file browser for gnome"
date: 2010-03-09
forum: Desktop Environments
---

### Post by doctordruidphd on 2010-03-09
I am actually running kubuntu, with the gnome desktop installed. All works well, except that I am getting kde's file browser (dolphin) instead of nautilus in gnome. There is a setting in kde for choosing the default browser, but that appears to be setting the browser for both desktops. Is there a way to reset gnome's configuration independent of kde, so that kde will use its own default browser, and gnome will use nautilus? So far I have not been able to find anything in gconf-editor that helps.

Edit: I should mention that this problem exists in both karmic and lucid.

---

### Post by inobe on 2010-03-09
a quick search

[http://forums.fedoraforum.org/showpost.php?p=1335297&postcount=5](http://forums.fedoraforum.org/showpost.php?p=1335297&postcount=5)

---

### Post by doctordruidphd on 2010-03-09
I saw that. Yes, that is the problem -- if you set kde to use "file browser", it will then use nautilus instead of dolphin. The idea here is to get gnome to use its default browser (nautilus), and kde to use its default (dolphin). So far, it seems to be that both use one or the other. I haven't been able to find where the configurations are getting set for both desktops.

---

