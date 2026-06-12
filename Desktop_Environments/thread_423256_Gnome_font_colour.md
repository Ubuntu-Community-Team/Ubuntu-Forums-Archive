---
title: "Gnome font colour"
date: 2007-04-25
forum: Desktop Environments
---

### Post by frylock on 2007-04-25
Hi there,


I've seen the post [http://ubuntuforums.org/showthread.php?t=47776](http://ubuntuforums.org/showthread.php?t=47776) but am wondering how i can specify only gnome clock on panel in notification area to have white font.


Specifically only in normal state without the mouse hovering over it. The link only provides for all text on panel.


Regards

---

### Post by frylock on 2007-04-26
So answer is 

```
 
style "panel-clock"
{
  fg[NORMAL] = "#FFFFFF"
}
widget "*.clock-applet-button.*" style "panel-clock"

```- add to (or create and add to) ~/.gtkrc-2.0

---

