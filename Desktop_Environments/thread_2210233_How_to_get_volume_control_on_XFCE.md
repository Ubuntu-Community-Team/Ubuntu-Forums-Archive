---
title: "How to get volume control on XFCE?"
date: 2014-03-09
forum: Desktop Environments
---

### Post by Steve_Corman on 2014-03-09
I am trying to determine how to get a volume control on my XFCE desktop.  Synaptic says xfce4-volumed is installed, but there is no "audio mixer" item on any of the add menus for the panels, nor is there anything in the application menus.  I tried launching it from a terminal, but nothing happens.

---

### Post by Frogs Hair on 2014-03-09
Install the xfce-goodies package which is not installed by default with the xfce session , log out and in and then check the add to panel menu.

---

### Post by Yellow Pasque on 2014-03-09
> **Steve_Corman said:**
> I tried launching it from a terminal, but nothing happens.

That means it's running. I think what you are really looking for is xfce4-mixer.

I personally use a package called volumeicon-alsa (though I build my own version from git).

---

### Post by Steve_Corman on 2014-03-10
Installed xfce-goodies, and still nothing in the menus.  This is not a huge issue as I found I can launch alsamixer from a terminal and make the adjustments.  When I did this it briefly showed a volume icon on the screen, so it's hiding in there somewhere.  

In addition I did have a bar at the top with time, applications, logout items.  It just appeared during some other things I was doing so I don't know how it got there, and after I restarted it is gone.  Any idea how I get that back?  Seems to be no option for it in desktop settings.  Sorry, kind of an XFCE newbie here--have only used KDE before.

---

### Post by Yellow Pasque on 2014-03-10
What version of (X)ubuntu are you running?
Try this:
```
sudo apt-get install volumeicon-alsa
killall xfce4-volumed
volumeicon&
```
Better?

Right-click on the new speaker icon, select preferences, and change 
```
xterm -e 'alsamixer'
```
to
```
xfce4-terminal -e 'alsamixer'
```
You can also adjust the other preferences to your liking.

---

