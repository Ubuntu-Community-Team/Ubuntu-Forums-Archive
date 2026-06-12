---
title: "full transparency"
date: 2009-09-13
forum: Desktop Environments
---

### Post by sHoIoKs on 2009-09-13
I've been working on setting up a transparent theme, but im having a couple issues.  first, i want to get the selected window on my window selector to be transparent, whereas now it is a solid grey which stands out against the clear panel.  my workspaces in the workspace switcher are also grey, and id like them to be transparent.  

[http://img10.imageshack.us/img10/9445/screenshotza.png](http://img10.imageshack.us/img10/9445/screenshotza.png)
you can see the grey on the bottom panel here

---

### Post by theZoid on 2009-09-13
I'll bump this for you because I'm trying to do the same thing but not sure if it's possible ????

---

### Post by steveneddy on 2009-09-15
Look at the screenshot.

This type of transparency is called RGBA and has to be coded into GTK.

Notice how on the gcalc and eye of gnome windows the main display areas are opaque and the surrounding is transparent.

You also will need to install gnome-color-chooser

```
sudo apt-get install gnome-color-chooser
```Also change colors on the theme manager or the gnome-color-chooser

true transparency directions are as follows for all other areas of the desktop:

> ## Also make panel and menus transparent

Open CCSM

Go to General Settings

Go to Tab - Opacity Settings

Settings as follows:

dock 67
Menu 90
DropdownMenu 92
popupmenu 93

Link: [http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)> ## make gnome bar true transparent

if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the advanced desktop settings util, just install it:
sudo apt-get install compizconfig-settings-manager

this will make entire panel transparent
Link to RGBA plug in:

[http://www.gnome-look.org/content/show.php/RGBA+Gtk%2B+module?content=100556]("http://www.gnome-look.org/content/show.php/RGBA+Gtk%2B+module?content=100556")

[http://www.cimitan.com/murrine/rgba-support/list](http://www.cimitan.com/murrine/rgba-support/list)

You have all of the tools now. Go install and tweak. Compiz has more settings for transparency.

these two desktop pics are full size so click the pic and study it for clues and cues.

Questions? ask on this thread and I'll find it again in a few days.

I've been doing this since the Beryl days and I know how to get most everything transparent.

When you do the transparent toolbar trick pull a small window like the terminal down past the bottom toolbar to check for transparency.

Good Luck

---

### Post by steveneddy on 2009-09-15
I just did this one for fun.

Looks like glass.

---

### Post by steveneddy on 2009-09-15
I should warn you that playing with this stuff on a work/school night is not advisable.

---

### Post by steveneddy on 2009-09-17
I hope I didn't waste my time posting this little bag of tricks.

---

### Post by theZoid on 2009-09-17
> **steveneddy said:**
> I hope I didn't waste my time posting this little bag of tricks.

Nope !  thanks  :):)

---

### Post by steveneddy on 2009-09-19
> **theZoid said:**
> Nope !  thanks  :):)

Well then, post some pics.

How you coming along?

Let's see where you are so far.

---

### Post by Rob_H on 2009-09-19
You might want to consider KDE, as well. Most themes in KDE 4 support some level of transparency.

---

