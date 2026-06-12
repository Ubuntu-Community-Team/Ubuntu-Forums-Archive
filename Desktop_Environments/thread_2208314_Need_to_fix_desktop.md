---
title: "Need to fix desktop"
date: 2014-02-27
forum: Desktop Environments
---

### Post by Donnie Love on 2014-02-27
I finally admitted defeat and updated to the latest and worst version of Ubuntu, this mobile version complete with giant kindergarten buttons on the left of the screen and everything else completely stripped away. I have this installed on a desktop computer and I want a real desktop environment. Is there anyway to fix it?

---

### Post by deadflowr on 2014-02-27
Which latest?

You can try
```
sudo apt-get install gnome-panel
```
when finished, logged out and in the login screen where you enter your password, look at the top right corner of that box and hopefully and Ubuntu-logo icon is there.
Click it and hopefully gnome classic, or something like that is listed.
Select the gnome(whatever it would be called) and then type your password.

This is close, though not completely the same, as the old gnome session.

---

### Post by Donnie Love on 2014-02-27
I don't know how to find out what number version this is. I don't know how to open a terminal window. I can't*** find anything.***

---

### Post by slickymaster on 2014-02-27
> **Donnie Love said:**
> I don't know how to open a terminal window. I can't*** find anything.***
You can either:
[LIST=1]
[*]Open the Dash by clicking the Ubuntu icon in the upper-left, type "terminal", and select the Terminal application from the results that appear.
[*]Hit the keyboard shortcut Ctrl-Alt+T.
[/LIST]
> **Donnie Love said:**
> I don't know how to find out what number version this is.
Now that you know how to open a terminal, open one and type the following in the prompt```
lsb_release -a && uname -r
```hit the Enter key and copy/paste the ouput to this thread.

---

### Post by Donnie Love on 2014-02-27
Thank you. In between freeze-ups, I managed to determine that this version is 13.10. Sure isn't very stable.

---

### Post by buzzingrobot on 2014-02-27
If your heart is in 2010, install the Mate desktop. (Instructions here: [http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download)).  Mate is the fork/recompilation/continuation of the Gnome 2 interface that the Gnome developers put out to pasture in 2011, forcing Canonical, and others who used Gnome 2, to find/create new interfaces. Mate changes the names of several core components to prevent conflicts with current Gnome components using the same names.  Otherwise, it's pretty much the same as Gnome 2 way back when. There has been some incorporation of GTK3 capability to allow users to run contemporary applications, and the next Mate release should be fully compatible with GTK3. (Gnome 2 was based on GTK2, and that isn't seeing much, if any, development these days.)

Much guidance and documentation about using Unity is available. For starters, tap the Super/Windows key and type "Help".  No question that Unity is a very different interface than old panel-based GUI's.  But, there's little to be gained by trying to use it without trying to *learn* how to use it on its own terms. It is not Gnome 2 and won't work if someone tries to pretend it is.

---

### Post by ibjsb4 on 2014-02-27
> **deadflowr said:**
> Which latest?

You can try
```
sudo apt-get install gnome-panel
```
when finished, logged out and in the login screen where you enter your password, look at the top right corner of that box and hopefully and Ubuntu-logo icon is there.
Click it and hopefully gnome classic, or something like that is listed.
Select the gnome(whatever it would be called) and then type your password.

This is close, though not completely the same, as the old gnome session.

I think this is the quick fix.  Use the "no-effects" session.

---

### Post by deadflowr on 2014-02-27
> **ibjsb4 said:**
> I think this is the quick fix.  Use the "no-effects" session.

As opposed to the long fix, I guess.

Seems to me that Unity might be too heavy for the users machine.
Or the machine needs some tweaking(drivers, etc)

Anyway, I don't even know if the gnome-panel command works for 13.10.
(probably does, but I do know it works for 12.04)

It'll at least give some sense of familiarity.

---

### Post by ibjsb4 on 2014-02-28
> **deadflowr said:**
> Anyway, I don't even know if the gnome-panel command works for 13.10.
(probably does, but I do know it works for 12.04)

It'll at least give some sense of familiarity.

Yep, works in 13.10; things (gnome) get changed around in 14.04.

---

### Post by buzzingrobot on 2014-02-28
> **deadflowr said:**
> 
Seems to me that Unity might be too heavy for the users machine.
Or the machine needs some tweaking(drivers, etc)



If the hardware is aging, specifically the graphics card, 3D accleration probably ought to be avoided, which would point the OP in the direction of XFCE/Mate/LXDE and away from Unity/Gnome/KDE.

---

