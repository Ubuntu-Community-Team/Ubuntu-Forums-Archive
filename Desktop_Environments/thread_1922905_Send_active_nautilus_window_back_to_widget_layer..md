---
title: "Send active nautilus window back to widget layer\."
date: 2012-02-09
forum: Desktop Environments
---

### Post by koohyar on 2012-02-09
Hey there everyone,
I've been exploring around compiz's widget layer (using screenlets) and I was wondering if I may be able to send the active nautilus window to the widget layer?! Say, I want to middle-click on the title bar of the a nautilus window and have it disappeared and sent back to my widget's layer. Does anyone know how one might be able to achieve this? I'm sure there's a way..there always has been! :)
Any help would be appreciated,
Thanks\.
[using oneiric]

---

### Post by koohyar on 2012-02-21
Solved it myself...wasn't that hard actually! :)
I just used xprop to grab a window's title and then passed it to compiz's widget layer plugin through gconftool-2. This way I wouldn't be even bound to the "active nautilus" window, but *any* window on the screen because xprop can grab any window's title!!
a simple file like this:
```
new="$(xprop WM_NAME | cut -d \" -f2)"
new="title="$new
old="$(gconftool-2 --get /apps/compiz-1/plugins/widget/screen0/options/match)"
target=$old" | "$new
gconftool-2 --type string --set /apps/compiz-1/plugins/widget/screen0/options/match "$target"
```
then all I had to do was to assign some key bindings to the file in CompizConfig Settings Manager.
Also added one for getting all the windows back to the normal layer with:
```
gconftool-2 --type string --set /apps/compiz-1/plugins/widget/screen0/options/match ""
```
Worked like a charm! :)\.

---

