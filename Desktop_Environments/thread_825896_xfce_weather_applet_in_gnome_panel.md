---
title: "xfce weather applet in gnome panel"
date: 2008-06-11
forum: Desktop Environments
---

### Post by timzak on 2008-06-11
Is this possible?  The xfce version is so much better than the gnome version.  It has more locations (I believe you can just type in a zip code instead of wading through menus of country->state->city), and has the ability to cycle through different weather stats visually right on the applet icon so you don't have to hover your mouse over it or click it to open a forecast window.

---

### Post by Robotman on 2008-07-03
I too would love to know how to replace the Gnome weather applet with the Xfce weather applet.  After just having installed Xubuntu on an old computer, I want to get all the great functionality of that weather applet on my Gnome desktop.  Anyone have any tips for swapping them?

EDIT: I see "xfce4-weather-plugin" in Synaptic Package Manager.  I'm guessing that's the cool applet in question.  Does anyone know how to do the swap?

---

### Post by pvincent on 2008-10-12
I am interested too.

The xfce weather applet is much better than its equivalent for gnome.
The 5-days forecast panel is such a good idea.

---

### Post by swisscow on 2009-12-13
Resurrecting this in case anyone has got an answer. Just returned to gnome after playing with xfce for a while and the weather applet in xfce is great. 

Any ideas anyone?

---

### Post by swisscow on 2009-12-14
bumpety bump

---

### Post by sisco311 on 2009-12-14
> **swisscow said:**
> Resurrecting this in case anyone has got an answer. Just returned to gnome after playing with xfce for a while and the weather applet in xfce is great. 

Any ideas anyone?

Use the [xfce4-panel]("apt://xfce4-panel") (click the link to install it). :)

To replace gnome-panel with xfce4-panel press Alt+F2 and run:
```
gconf-editor
```

go to desktop/gnome/session/required_components and change the value of *panel* from gnome-panel to xfce4-panel.


[xfce4-xfapplet-plugin]("apt://xfce4-xfapplet-plugin") (click the link to install it) allows you to use Gnome applets inside the xfce4-panel just as they are used inside the gnome-panel.

---

### Post by swisscow on 2009-12-14
Many thanks, will give it a go.

No way of just adding it to the gnome panel then?

---

### Post by criticalsmile on 2011-01-30
Seriously, let's get this app going on just Gnome and not XFCE. I hope Wayland get's something similar or better. :-D

---

### Post by masinick on 2011-11-26
As of about a month ago, the Xfce weather applet broke, and its broken condition shows up in most distributions.  Apparently the weather feed changed requirements.  One report indicated that the Weather.com source now requires some kind of subscription that caused the algorithm being used to break, causing "No Data" to be displayed.

One other report indicates that there is a change in the Git area for a fix; hopefully that change will be tested and built for Xfce-based systems soon.

---

