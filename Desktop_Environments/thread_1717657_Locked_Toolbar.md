---
title: "Locked Toolbar"
date: 2011-03-30
forum: Desktop Environments
---

### Post by Stan Bennett on 2011-03-30
I am kind of new to Linux so please be kind. I have been working for the last three months with Ubuntu 10 on a destop. Doing just fine and loving it. I decided to try a new position for the toolbar that sits at the top of the screen. I did a right click and moved it to the right side of the scree, didn't like the look of that. Right click on the bar and moved it to the left, didn't like that either, so moved it to the bottom. having done all that I thought I could put it back at the top but alas, I can not right click on the Toolbar. It seems as though the two bars are fighting each other at the bottom of the screen.I would like to go back to the default position at the top of the screen.
I do have a terminal window available to me on the desktop so if I could find out the command line to type in, I should be able to reset my tool bar. Being new I have no idea what this command would be.
Any help would be very appreciated. If no help comes soon I will reload the whole OS and remember never to move the toolbar again.
Thanks
StanB

---

### Post by Frogs Hair on 2011-03-30
This works for some users to restore panels to default .```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Megaptera on 2011-03-30
Hi Stan B,

For the future you might find this useful:
"PanelRestore, allows you to quickly and easily restore the default Gnome panels in Ubuntu and to backup and restore your existing custom panel configurations."

[http://helpdeskgeek.com/linux-tips/e...els-in-ubuntu/](http://helpdeskgeek.com/linux-tips/e...els-in-ubuntu/)

---

