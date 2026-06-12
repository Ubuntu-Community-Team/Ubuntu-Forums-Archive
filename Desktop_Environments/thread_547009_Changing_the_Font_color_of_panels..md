---
title: "Changing the Font color of panels."
date: 2007-09-09
forum: Desktop Environments
---

### Post by grungebunny on 2007-09-09
Hello i'm using Ubuntu 7.04 in the Gnome environment.

I have my panels set to total transparency and I have a dark background image.. i'd like to change my panel fonts a lighter color so they will be easier to read.. a search for changing them only yielded a fix on making a .gtkrc-2.0 file.. but the post was quite old... I tried that and the font color still did not change.

Does anyone have any suggestions?

---

### Post by tatrefthekiller on 2007-09-09
Hello. I'm just trying to do the same thing...

You visited this link ?
[http://brentroos.com/2006/07/07/change-gnome-panel-text-color/](http://brentroos.com/2006/07/07/change-gnome-panel-text-color/)

The blog suggests to edit the .gtkrc-2.0 file in the home directory, but I can't find this one. Instead I found .gtkrc-1.2-gnome2 that was only containing this line :

include "/home/yann/.gtkrc.mine"

Some help could be grateful !!!

EDIT : It worked : I used the .gtkrc-2.0 file with this inside (to change the font color) :

style "panel"
{
 fg[NORMAL] = "#D6E6FF"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"

Then type "killall gnome-panel" to reload it.

---

### Post by grungebunny on 2007-09-09
yes your script worked when all others have failed yay

---

### Post by scxtt on 2007-09-09
gnome 2.18 can do this from w/in the theme manager ... my only gripe is it effects the tooltips too, so if i change it to white, i can barely see them on the yellow background ... i'm sure there's a solution for this (editing in a similar method above, or stopping tooltips from popping up).

---

### Post by mcduck on 2007-09-10
> **scxtt said:**
> gnome 2.18 can do this from w/in the theme manager ... my only gripe is it effects the tooltips too, so if i change it to white, i can barely see them on the yellow background ... i'm sure there's a solution for this (editing in a similar method above, or stopping tooltips from popping up).

No, it can't. You can only change some colors from there, and even that only if you use a theme built to support changing colors. But you can't change any specific color like panel font color or menu background color.

Anyway, to change tooltip background put the following piece of code into ~/gktrc-2.0
```
style "tooltips"
{
  bg[NORMAL] = "#ADBCC6"
}

widget "gtk-tooltips" style "tooltips"
```

---

### Post by scxtt on 2007-09-10
for what the opening poster wanted to do (i've wanted to do the same thing) - the theme manager can accomplish it ... i.e. transparent panel, black background, theme manager can set white fonts for the panel ...

---

### Post by mcduck on 2007-09-11
> **scxtt said:**
> for what the opening poster wanted to do (i've wanted to do the same thing) - the theme manager can accomplish it ... i.e. transparent panel, black background, theme manager can set white fonts for the panel ...

Well, true. But he'd also end with white fonts in applications as the Theme Manager doesn't have a specific setting for panel font color.. Not very nice if the GTK theme isn't a dark one :)

---

### Post by scxtt on 2007-09-11
you're right :) - i was only mildy happy w/ the results of doing it via the theme manager - but it was def. a step up from 2.16 where i couldn't do it @ all ...

---

### Post by Phurious on 2007-11-24
> **tatrefthekiller said:**
> Hello. I'm just trying to do the same thing...

You visited this link ?
[http://brentroos.com/2006/07/07/change-gnome-panel-text-color/](http://brentroos.com/2006/07/07/change-gnome-panel-text-color/)

The blog suggests to edit the .gtkrc-2.0 file in the home directory, but I can't find this one. Instead I found .gtkrc-1.2-gnome2 that was only containing this line :

include "/home/yann/.gtkrc.mine"

Some help could be grateful !!!

EDIT : It worked : I used the .gtkrc-2.0 file with this inside (to change the font color) :

style "panel"
{
 fg[NORMAL] = "#D6E6FF"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"

Then type "killall gnome-panel" to reload it.

Well, I have a question; where did you finally find the .gtkrc-2.0 file?  I do not have one in my home directory, only a .gtkrc-1.2-gnome2 as you mentioned above.  If I create the .gtkrc-2.0 and add the entries as prescribed it does nothing?  Any ideas? :confused:

---

### Post by mcduck on 2007-11-24
> **Phurious said:**
> Well, I have a question; where did you finally find the .gtkrc-2.0 file?  I do not have one in my home directory, only a .gtkrc-1.2-gnome2 as you mentioned above.  If I create the .gtkrc-2.0 and add the entries as prescribed it does nothing?  Any ideas? :confused:

Just create the file if it doesn't exist. And then you need to log out & back to see the changes.

---

### Post by Phurious on 2007-11-24
Perfect!  Thanks for the reply!!  I had killed gnome-panel, as stated above, but did not see the changes; guess I should have thought to log out!   :popcorn:

---

