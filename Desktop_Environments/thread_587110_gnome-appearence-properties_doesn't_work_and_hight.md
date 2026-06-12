---
title: "gnome-appearence-properties doesn't work and hight cpu usage"
date: 2007-10-22
forum: Desktop Environments
---

### Post by lugburz on 2007-10-22
It's the 2nd time that something like this happen to me.

I installed from scratch, but conserving the data in my home directory, kubuntu gutsy, then I switched to ubuntu and gnome.

All work reasonably well but when I try to use gnome-appearance-properties to change some graphical configuration my laptop start to have a very hight cpu usage (100% for one of the cores) and the configuration window is completely stuck.

This is very strange and very annoying, being also the second time that happen I'm starting to think not good things about ubuntu :-(

---

### Post by scottmuz on 2007-10-22
Got exactly the same issue, although I did an upgrade from fiesty.

---

### Post by ayoli on 2007-10-22
I think having a big cpu usage when changing themes is normal, but if it doesn't work try this (in a terminal) :
```
mv .gconf .gconf.backup
```
then logout and login

---

### Post by lugburz on 2007-10-23
I'll try but I don't think that this can be considered "normal", in my opinion it's a bug that is not corrected from 6 months. :(

---

### Post by lugburz on 2007-10-23
This solution doesn't work for me: gnome-appearance-properties continues to have an high cpu usage but down't have the capability to show anything.

I gained only some new cool feature when a new window appear but I lost evolution configuration, I prefer to restore the old .gconf and probably the only soution is move to KDE.

---

### Post by ayoli on 2007-10-23
The "normal" cpu usage is a bug, I said normal as I've seen this high cpu usage on every box with ubuntu feisty/gusty.
btw, gnome-appearance-properties works here, you may try to launch it from a terminal and tell us about possible errors in the terminal output.

---

### Post by brainiac on 2007-10-23
i can confirm this one.. since yesterday switching themes with the theme.manager brings my desktop down (high cpu usage and nothing responds anymore) only fixable by rebooting and switching with the gtk-theme-switcher2.

this behaviour only occours when switching to non standard themes.. like murinne or aurora

---

### Post by lugburz on 2007-10-23
In my installation I don't have ant gtk-theme-switcher2 program, in which package is?

I'm using a standard theme: human.

---

### Post by kugrian on 2007-10-23
I had a similar problem after installing KDE, then switching back to GNOME.  Found [this thread]("http://ubuntuforums.org/showthread.php?t=571474&highlight=gutsy+GTK_WIDGET_VISIBLE") right after reading the issues here, and wonder if the problems might be similar.  

The fix that worked for me anyway was uninstalling gtk-qt-engine.

---

### Post by frbe0101 on 2007-10-25
That fixed it, I guessing Qt setting won't work anymore but that will not be a problem right?

---

### Post by LostinSpacetime on 2008-06-01
I just wanted to add that I have the same isue (100% CPU usage immediatly after starting gnome-appearance-properties) and this solution doesn't work for me. However, beside the slowness and that it's pretty hard to change the desktop background, gnome-appearance-properties seem to do it's job. 

Please post if anyone has the same problem.

---

### Post by bengoza on 2008-06-04
Yes I am having this same problem. It just started tonight. It's only when trying to change the backgrounds. I'll click on one and it won't do anything. gnome-appearance-properties' CPU usage is about 95%. The only thing I changed recently was I tried to install Quake 2. WTF is going on?

Edit: This doesn't fix the problem, but if you're stuck on a background you don't like (I was) you can use the arrow keys to select a different one.

---

### Post by jagrav on 2008-06-04
Same problem here in Ubuntu Hardy. Happened after the last bunch of updates perhaps. Thanks Begoza for the tip on using the arrow keys.

---

### Post by ShodanjoDM on 2008-06-04
Launchpad bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/236778](https://bugs.launchpad.net/ubuntu/+source/gnome-desktop/+bug/236778)

---

