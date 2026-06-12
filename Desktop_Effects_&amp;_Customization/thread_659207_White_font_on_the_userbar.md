---
title: "White font on the userbar ?"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by marcon00 on 2008-01-05
how can i change the color of userbar to white ? i applied dark bkg of my panel, and it would look neat with white font :) thanks in advance ..

---

### Post by aJayRoo on 2008-01-05
I like to use a white font (well, its light grey actually, looks a bit better I think) for my panels so that I can have a dark background on them. The procedure for doing this is relatively simple:

1) Edit/create a gtkrc-2.0 file:
```
gedit ~/.gtkrc-2.0
```
inside this file insert the following lines:
```
# comment following line to revert to normal panel font style
include "/home/USERNAME/.gnome2/panel-fontrc"
```
making sure to replace USERNAME with your user name. Save and close the file.

2) Edit/create a panel font file:
```
gedit ~/.gnome2/panel-fontrc
```
inside this file include the following:
```
style "my_color"
{
    fg[NORMAL] = "#E2E2E2"
}
widget "*PanelWidget*" style "my_color"
widget "*PanelApplet*" style "my_color"
```
Save and close the file.

You will need to log out and back in again before changes take effect. The colour is defined by its hexadecimal representation, in this case #e2e2e2, for white you could change that to #ffffff. Hope that helps.

---

### Post by marcon00 on 2008-01-06
Thanks Dude ! Worked like a charm :D !!!

---

