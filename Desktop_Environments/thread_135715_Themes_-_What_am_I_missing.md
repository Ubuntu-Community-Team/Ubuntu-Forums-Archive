---
title: "Themes - What am I missing?"
date: 2006-02-24
forum: Desktop Environments
---

### Post by suRoot on 2006-02-24
I've been using Linux for a long time, in server farms, but I have to admit that I know squat about Gnome or KDE.

I'm just playing around trying to change my theme.  Some themes that I download from [http://www.gnome-look.org](http://www.gnome-look.org) or [http://art.gnome.org](http://art.gnome.org), work properly.  That being, they look exactly like the screenshots provided on the web sites.

Other themes (namely the ones I usually seem most interested in!!), don't seem to work at all.  For example - the "Darker Theme" I found on gnome-look

[IMG]http://www.gnome-look.org/content/pre1/32768-1.jpg[/IMG]

that's what it's supposed to look like.

However, looking at the screenshot I've attached, you can see my results are very different.

My question is, what am I missing?  It doesn't seem like rocket science - either extract the archives to ~/.themes or drag & drop them in the theme manager.  What am I doing wrong?

---

### Post by andrewsawyer on 2006-02-24
It is a GTK theme.  From memory, GTK themes only changes things like buttons and scroll bars.  I assume there would be a matching Metacity theme to use with it - Metacity themes change the window borders (max/min/close) and things like that.

---

### Post by magomago on 2006-02-24
[http://www.gnome-look.org/content/show.php?content=32326](http://www.gnome-look.org/content/show.php?content=32326)

try that metacity theme in combonation with the font you want.  

You know if you want the taskbars black...that is what I've never been able to figure out.  Even if I right click on it and modify the color only the icons that I add will actually change..the other parts don't.  So if anyone wants to chime in alet us know we would appreciate it

---

### Post by Spano on 2006-02-24
Try installing gtk-theme-switch using Synaptic or from terminal:
```
sudo apt-get install gtk-theme-switch
```
I don't know if it will show up in Gnome menu but you can execute from terminal using:
```
/usr/bin/switch
```for GTK 1. themes
```
/usr/bin/switch2
```for GTK 2. themes
I use gtk-theme-switch in Fluxbox and I think it works in Gnome as well.

---

