---
title: "Compiz opacity 12.10   Gnome 3.6 &amp;&amp; MATE"
date: 2013-02-22
forum: Desktop Environments
---

### Post by pages on 2013-02-22
Hi all ,

Came back to linux after a long absence and just trying to set up my config to how I used to have it.
I'm running 12.10 32bit 
Using Gnome 3.6  ( the fall back version i believe) and I set up compiz but can't seem to find an option for effecting the opacity settings.

I've done searches on this and most issues seemed to have been resolved by looking in the accessibility sections
This however will not solve the issue since it's not there :/

Was thinking it might have something to do with compatability between gnome 3.6 and compiz so I tried using the gnome 2 ( MATE) to try and see if it could work but neither worked.



Screenshots of both 
Gnome 3.6
[http://i47.tinypic.com/25i55hx.png](http://i47.tinypic.com/25i55hx.png)

MATE
[http://i49.tinypic.com/2wehtz4.png](http://i49.tinypic.com/2wehtz4.png)

---

### Post by wildmanne39 on 2013-02-22
*Thread moved to **Desktop Environments**.*

---

### Post by grahammechanical on 2013-02-22
Try looking in the Ubuntu Unity Plugin. You should find an option to set the opacity of the Unity Launcher and the Unity top panel. Did you notice that I made a point of saying "Unity." Compiz is the compositing/window manager that the Unity user interface sits on. The Compiz Configuration Settings Manager (CCSM) will make adjustments to Compiz and Unity.

I am not sure how well adjustments in CCSM wil have an effect on Gnome fallback. I have never tried it.

Regards.

---

### Post by pages on 2013-02-22
Just in case other people hit the issue 

this website helped out [http://www.jameswigley.com/2012/04/27/making-ubuntu-unity-look-beautiful-by-enabling-transparency/](http://www.jameswigley.com/2012/04/27/making-ubuntu-unity-look-beautiful-by-enabling-transparency/)

```
sudo apt-get install compizconfig-settings-manager compiz-plugins

sudo apt-get install compiz-gnome dconf-tools
```

---

