---
title: "Xfce compositor issues"
date: 2008-02-23
forum: Desktop Environments
---

### Post by cardinals_fan on 2008-02-23
I have always had problems with the Xfwm4 compositor. This isn't just a Xubuntu problem, as I have also experienced it on Zenwalk.  When I enable the compositor, things go fine... at first.  After some time, or whenever I first log in, the icons on the desktop get screwed up and my panels go crazy.  I will link to pics of my desktop both working and ugly.  I have the propriety drivers installed on my Nvidia card, which runs Compiz Fusion with no problems, so this shouldn't be an issue.  Compositing is enabled in Xorg.conf.  Ideas?


How it looks when things go wrong:

[[IMG]http://img246.imageshack.us/img246/1707/comppiczo3.th.jpg[/IMG]](http://img246.imageshack.us/my.php?image=comppiczo3.jpg)

Note that this does not show any panel issues... they occur less frequently and I couldn't reproduce them accurately.

How it should look:

[[IMG]http://img215.imageshack.us/img215/9936/nocompvz6.th.jpg[/IMG]](http://img215.imageshack.us/my.php?image=nocompvz6.jpg)

---

### Post by fracturedmorals on 2008-02-23
DISCLAIMER: This may be erroneous....so if it doesn't work then...well....I tried

Is conky set to double buffer? Did you use conky on both Zenwalk and Xubuntu?

I'm not entirely certain of this, but I believe that XFCE's compositing manager is very similar to, if not based on, xcompmgr and I seem to recall getting similar behaviour on openbox while I had both conky (Set to double buffering and set to be part of the desktop window) and xcompmgr running at the same time. I ended up with pretty dropshadows and transparent windows....that flickered and acted weird. :(

It might be worth seeing how it acts without conky running and just using a screenlet instead (I know of a nice sysmon one that comes with whise's 0.12 version [http://gnome-look.org/content/show.php/Screenlets+0.0.12+final+rev+174?content=73346]("whise's 0.12 version ")

Anyways....that's just my 2 cents....

--Ian

---

### Post by cardinals_fan on 2008-02-23
[QUOTE=fracturedmorals]DISCLAIMER: This may be erroneous....so if it doesn't work then...well....I tried

Is conky set to double buffer? Did you use conky on both Zenwalk and Xubuntu?

I'm not entirely certain of this, but I believe that XFCE's compositing manager is very similar to, if not based on, xcompmgr and I seem to recall getting similar behaviour on openbox while I had both conky (Set to double buffering and set to be part of the desktop window) and xcompmgr running at the same time. I ended up with pretty dropshadows and transparent windows....that flickered and acted weird.

It might be worth seeing how it acts without conky running and just using a screenlet instead (I know of a nice sysmon one that comes with whise's 0.12 version [http://gnome-look.org/content/show.php/Screenlets+0.0.12+final+](http://gnome-look.org/content/show.php/Screenlets+0.0.12+final+) rev+174?content=73346

Anyways....that's just my 2 cents....

--Ian[/QUOTE]

Thanks for the reply, I might try that.  However, I will take my conky over compositing.

---

