---
title: "Linux Program like MaxTo"
date: 2009-03-02
forum: General Help
---

### Post by Atrus6 on 2009-03-02
Is there any program available for Ubuntu that offers the same functionality as [MaxTo]("http://www.maxto.net")?

---

### Post by radischem on 2009-05-02
Hallo

Schön, das jemand die gleichen Sorgen hat ;)

Habe gerade das hier gefunden, wenn auch noch nicht probiert:

[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/](http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/)

Abgesehen davon finde ich es sehr kompliziert und nicht annähernd so sorgenfrei in der Benutzung wie MaxTo.

Hoffentlich hat jemand anderes noch eine Idee..


:: Sorry, I sometimes don't get that I read something in English...

I am also looking for such a programme. The above link is supposed to solve the problem with sizing windows. Haven't tried it yet though.

Would appreciate if someone would know a programme similar to MaxTo anywho.

radischem

---

### Post by thefluxster on 2009-11-16
Ditto - I use this app heavily in Windows and would love something similar for Gnome.

---

### Post by thefluxster on 2009-12-02
> **radischem said:**
> ...I am also looking for such a programme. The above link is supposed to solve the problem with sizing windows. Haven't tried it yet though...


Two issues with this solution:
1. Apparently not recommended with Compiz.
2. Doesn't create "zones" on your desktop that things magically snap into when maximized.  MaxTo is GREAT at this.

---

### Post by thefluxster on 2009-12-02
Actually, I found a decent option in Compiz.  Open the settings manager (need to install compiz-settings-manager first) and go to the section "Window Management" and then "Grid".  Turning it on lets you hit hotkeys to reposition windows in an imaginary grid on your desktop.  Haven't tried with multiple monitors yet, but it worked decent for my laptop.  The screen is so small I usually only split it once vertically anyway.  This works for me.

---

### Post by sessentaecinco on 2009-12-21
> **thefluxster said:**
> Ditto - I use this app heavily in Windows and would love something similar for Gnome.

What you're looking for is [Parcellite]("http://parcellite.sourceforge.net/").

```
sudo apt-get install parcellite
```

---

### Post by stinkeye on 2009-12-22
Compiz has a tiling plugin in the compiz-fusion-plugins-unsupported package.
You need to get the package from the [_[COLOR="DarkRed"]compiz ppa[/COLOR]_]("https://launchpad.net/~compiz/+archive/ppa?field.series_filter=")
Only download the compiz-fusion-plugins-unsupported package (0.8.3+git20090911-1ubuntu1) from this repo 
and then disable the repo in your sources list because you'll loose your animation add-ons if you update some of the other compiz stuff.
Worked fine for me on jaunty and now karmic.
It will tile all open windows vertically, horizontally or in a grid.

Gnome-do also has a simple window tiler if you enable the Window Manager plugin.
To use just type in tile ,hit tab then down arrow and you'll see some options.

or

If you want more control over the size and position of the window use wmctrl
```
sudo apt-get install wmctrl
```
This code will resize and position an active window
```
wmctrl -r :ACTIVE: -e 0,400,250,890,560
```
where the numbers represent in order desktop,x screen position,y screen position,x window size,y window size
You can then use ccsm > commands to set an edge binding to that command.
By dragging a window to the edge so the mouse touches the edge the command will execute thereby resizing and positioning the window.
In ccsm > general options change the edge trigger delay to around 700 so
you don't accidently trigger it all the time.
Alternatively you could install easystroke and bind the wmctrl commands to mouse gestures.
Plenty of options to create your own enviroment.

 

> **sessentaecinco said:**
> What you're looking for is [Parcellite]("http://parcellite.sourceforge.net/").

```
sudo apt-get install parcellite
```
Parcellite is a  clipboard manager.

---

