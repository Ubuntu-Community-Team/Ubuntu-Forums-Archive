---
title: "LXDE Desktop task manager?"
date: 2009-10-06
forum: Desktop Environments
---

### Post by asianette on 2009-10-06
Is there some kind of desktop task manager that shows open windows and such? I don't want a bottom panel with the window list. I don't want Conky, either. I just want a little widget-type box-thing that shows the open windows (so that I can have a terminal open all the time running htop). Is there such a thing?

---

### Post by XubuRoxMySox on 2009-10-06
Hi!

The place to ask that might be the [LXDE forums]("http://forum.lxde.org/index.php"). I haven't actually needed such a thing even though LXDE has been my chosen d.e. for a few months.

I know that in PCManFM you can choose Edit>Preferences, under the Desktop tab, you can check all three boxes, and let PCManFM manage the desktop for you. If that helps.

But open windows (and minimized ones) ordinarily just show up in the bottom task bar.

Hoping I've helped a little,
Robin

---

### Post by kerry_s on 2009-10-06
> **asianette said:**
> Is there some kind of desktop task manager that shows open windows and such? I don't want a bottom panel with the window list. I don't want Conky, either. I just want a little widget-type box-thing that shows the open windows (so that I can have a terminal open all the time running htop). Is there such a thing?

how about using a drop down terminal like tilda or maybe urxvt on the background?
[http://wiki.archlinux.org/index.php/Openbox#Urxvt_in_the_background](http://wiki.archlinux.org/index.php/Openbox#Urxvt_in_the_background)

---

### Post by asianette on 2009-10-06
> **kerry_s said:**
> how about using a drop down terminal like tilda or maybe urxvt on the background?
[http://wiki.archlinux.org/index.php/Openbox#Urxvt_in_the_background](http://wiki.archlinux.org/index.php/Openbox#Urxvt_in_the_background)

I set up tilda. I am trying to run a shell script that opens tilda and then runs htop from it, but I don't know how to pass commands to Tilda. Help?

---

### Post by kerry_s on 2009-10-07
> **asianette said:**
> I set up tilda. I am trying to run a shell script that opens tilda and then runs htop from it, but I don't know how to pass commands to Tilda. Help?

use "man tilda" to see the instruction pages.
looks like:
**tilda -c htop**

---

### Post by asianette on 2009-10-07
> **kerry_s said:**
> use "man tilda" to see the instruction pages.
looks like:
**tilda -c htop**

I got it working, and yes, it was ```
tilda -c htop
```

Then I put a .desktop file in /etc/xdg/autostart

---

### Post by kerry_s on 2009-10-07
> **asianette said:**
> I got it working, and yes, it was ```
tilda -c htop
```

Then I put a .desktop file in /etc/xdg/autostart

you know watching that thing is not healthy. :lolflag:
relax & enjoy your computer, play games, watch movies, chat with people. if theres a problem you'll feel it, remember all that stuff takes resources away from more important things, the system only needs to be monitored if you feel something is wrong.

i only open it when i get a slow down & want to see whats going on, most of the time it's usually just that updatedb cron job, but i like to make sure. :)

---

