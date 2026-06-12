---
title: "Firefox, exaile etc all messed up"
date: 2010-01-19
forum: Desktop Environments
---

### Post by blazemore on 2010-01-19
Attached is what my GTK applications look like on KDE.
The GTK style settings confuse me, as there's "GTK Appearance" and "GTK Style", both making me choose between "qtcurve" and "qt4"
I've tried every combination. This affects all GTK applications, not just Firefox.
I can see what the problem is; defauly "Oxygen" colours are being used, not the ones that I have applied to KDE apps.

---

### Post by Zorael on 2010-01-19
I think you have a mix of new and old packages. There should only be a GTK+ Appearance tab, which (in Karmic, at least) you get from the **kcm-gtk** package.

Try this in a terminal and see if it lists any other package.
```
$ dpkg -S /usr/share/kde4/services/*gtk*
```

Also, what is the contents of your **~/.gtkrc*** file(s)? Quick and dirty oneliner;
```
$ for file in ~/.gtkrc*; do echo "$file:"; cat $file; echo "---"; done
```

---

### Post by blazemore on 2010-01-19
james@james-desktop ~ $ for file in ~/.gtkrc*; do echo "$file:"; cat $file; echo "---"; done
/home/james/.gtkrc-2.0-kde4:
include "/usr/share/themes/QtCurve/gtk-2.0/gtkrc"
---

This is after I reinstalled, and yes, only one remains.
However, changing colours for KDE does not change the colours for GTK, even if I restart the GTK app.

---

### Post by Zorael on 2010-01-19
Is it being exported then, in **~/.kde/env/gtk2-engines-qtcurve.rc.sh**?
```
$ cat ~/.kde/env/gtk2-engines-qtcurve.rc.sh
#!/bin/bash

# Make sure our customised gtkrc file is loaded.
export GTK2_RC_FILES=$HOME/.gtkrc-2.0-kde4
```
As far as I understand (and do correct me if I'm wrong), it should inherit the KDE coloring if the QtCurve engine is in use. That doesn't really explain why it would keep using Oxygen coloring though.

Another thing you could check is whether this happens if you create a new (dummy) user. If it works fine there, there's probably something up with your **~/.kde**.

---

