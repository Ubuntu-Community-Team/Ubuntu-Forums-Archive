---
title: "Updates demolished my desktop environment..."
date: 2009-02-21
forum: Desktop Environments
---

### Post by Lupusceleri on 2009-02-21
Heyas,

I ran the Adept updater today (I have the repos to get KDE4.2 and AmaroK 2.0 and MediBuntu installed on top of the standard repos), and it seems to have messed up my Kubuntu install. From what I remember looking over the list of updates quickly, amongst 30 other updates, it removed something along the lines of a KDE window manager bundle pack (not sure?) and installed a zerg of new updates.

So I figured that the repo knows best, and hit apply changes. Stupid!

Now whenever I log in, my screen turns black right after filling in the password and hitting enter. I still see my mouse, and I can move my mouse. If I hit CTRL-11 (the shortcut for the KWin desktop cube) it shows me the two KDE logos above eachother, but the desktops itself are not there.

Maybe plasma doesn't start up anymore? I'm honestly at a loss as to how to fix this thing. One of the first steps should be to get into a terminal (I wonder how, there's nothing to click on). Any ideas?

Thank you,

Martijn.

---

### Post by taurus on 2009-02-21
At the GUI login screen, press <Ctrl><Alt>F2 to get to a console and log in with your username and password.  Then, reinstall kubuntu-desktop and see if it gets back where it was before.

```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```
To get back to GUI login screen after everything has been installed, press <Alt>F7.

---

### Post by Lupusceleri on 2009-02-21
That kind of poses a problem, I have a WLAN connection to the internet and the network manager doesn't seem to start up when I log in to the CLI environment rather than the graphical environment. It's the default network manager Kubuntu has.

Know any way to connect to the WLAN or should I just lug my PC downstairs for an oldschool network cable? :)

PS: Thanks for the quick reply.

---

### Post by taurus on 2009-02-21
So if you log in to your desktop, do you see a dialogue when you press <Alt>F2?  If you do, type in **konsole** to bring up a terminal and then run those commands to reinstall your KDE.

---

### Post by Lupusceleri on 2009-02-21
> **taurus said:**
> So if you log in to your desktop, do you see a dialogue when you press <Alt>F2?  If you do, type in **konsole** to bring up a terminal and then run those commands to reinstall your KDE.

ALT+F2 does nothing, sadly. Not when I log in like I would normally, not if I log into the CLI using CTRL ALT F2.

Sounds like I'm going to lug the PC down.

---

### Post by Lupusceleri on 2009-02-21
Thank you very much sir, that solved my problems. :D

I did have to connect the PC to an oldschool cable though. Marking as solved, can't find the thanks button anymore though.

---

