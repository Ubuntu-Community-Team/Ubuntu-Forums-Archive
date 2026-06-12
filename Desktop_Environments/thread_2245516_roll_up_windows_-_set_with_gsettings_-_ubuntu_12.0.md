---
title: "roll up windows - set with gsettings - ubuntu 12.04"
date: 2014-09-24
forum: Desktop Environments
---

### Post by rrob on 2014-09-24
Hi, how to set shade with mous wheel on title in Ubuntu 12.04 via gsettings?

In gconf-editor is it in /apps/gwd/ mouse-wheel-action=shade

But in gsettings i cant find it.

gsettings get org.compiz.gwd mouse-wheel-action - does not exist

I have also tryed:
gsettings list-recursively | grep gwd
gsettings list-recursively | grep mouse-wheel-action
but without success.

In Ubuntu 12.10+ works this:
gsettings set org.compiz.gwd mouse-wheel-action "shade"

Thanks

---

### Post by rrob on 2014-09-24
Or, how to translate "paths" between gsetings gconftool-2 gconf-editor ....

Im using 12.04.5 with trusty kernel because its last realy working version. With newer one I have lot of troubles on many computers. Most often it starts to black screen.

---

### Post by deadflowr on 2014-09-24
```
gconftool-2 --set --type string /apps/gwd/mouse_wheel_action shade
```
I guess that's what you want....

Some fun gconftool options
gconftools-2 --all-dirs / = list the top directory 
gconftools-2 --all-dirs /apps = list the sub-directory in /apps 
and something like 
gconftools-2 -R /apps

and it'll usually bark about needing a type when trying to set, so
gconftool-2 --get-type /path, excluding the actual value setting; ie, shade.
then add the type option like above.

--unset doesn't seem to care about types, go figure.

I hope this helps.
I'm still learning these things myself.

---

### Post by CantankRus on 2014-09-24
According to my notes, from 11.10 the setting is
```
gsettings set org.compiz.gwd mouse-wheel-action shade
```
but maybe it is still in gconf as **deadflowr** suggested.

In 14.04 the window decorations are managed by the unity plugin.
You can see this in 14.04 because CCSM shows a decorations tab in the 
unity plugin.

If 12.04 is now using this version of  compiz, shade may no longer
work when running unity.

Shade is still available in my flashback sessions as they use
**gtk-window-decorator** for decorations.

---

