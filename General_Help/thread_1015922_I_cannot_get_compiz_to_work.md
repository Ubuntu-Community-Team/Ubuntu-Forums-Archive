---
title: "I cannot get compiz to work"
date: 2008-12-19
forum: General Help
---

### Post by M3nsah on 2008-12-19
please disregard my double post

---

### Post by stderr on 2008-12-19
To check if Compiz is running you can do 

```
ps aux | grep compiz
```

If nothing is returned, it's not running. If it returns a compiz process, it's running. 

Did you also install the Compiz Config Settings Manager? It's a nice graphical configuration app which enables you to customise your Compiz configuration to your liking. 

```
sudo apt-get install compizconfig-settings-manager
```

You can then launch that from System -> CompizConfig Settings Manager. Settings changes take effect immediately.

---

### Post by Kevbert on 2008-12-19
Welcome to Ubuntu.
What's your graphics card ? If you have ccsm (as suggested by sterr in the previous post) you may be able to run compiz and get the cube. ATI, Nvidia and Intel cards are supported and someone has even got a S3 card to work.
You may need to run compiz-check which can be found [[COLOR="Red"]here[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check").

---

### Post by stderr on 2008-12-19
> **Kevbert said:**
> You may need to run compiz-check which can be found [[COLOR="Red"]here[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check").

:grin: bookmarked! That's going to be handy!

---

### Post by Kevbert on 2008-12-19
> **stderr said:**
> :grin: bookmarked! That's going to be handy!

You may also want to take a look at the Compiz-fusion [[COLOR="Red"]forum[/COLOR]]("http://forum.compiz-fusion.org/") for loads of extras as well as [[COLOR="Red"]Gnome-look[/COLOR]]("http://gnome-look.org/") for other goodies.

---

### Post by M3nsah on 2008-12-19
ok, i have determined that compiz is running, but i still do not see any effects. i have a geforce 7400go nvidia card. i think i have the driver working properly becuase i have the restricted drivers thing showing

---

### Post by stderr on 2008-12-19
> **Kevbert said:**
> You may also want to take a look at the Compiz-fusion [[COLOR="Red"]forum[/COLOR]]("http://forum.compiz-fusion.org/") for loads of extras as well as [[COLOR="Red"]Gnome-look[/COLOR]]("http://gnome-look.org/") for other goodies.

Cheers Kevbert, I may well peruse the compiz forums later. Problem is I can while away days checking forum posts :)

M3nsah, have you enabled any of the effects in CCSM? For example, start CCSM, then tick one of the boxes - say 'Enhanced Zoom Desktop'. The default mapping for that particular module is META + MOUSEWHEELUP to zoom in. You use META + MOUSEWHEELDOWN to zoom out.

META is the Windows key, and is sometimes also called SUPER.

Let us know if that has any effect...

---

### Post by Kevbert on 2008-12-19
You should have a menu item under System-Preferences which will be Advanced Desktop Effects or Compiz Configuration Settings Manager (depending on what version of Ubuntu you are using).
Under General Settings-Desktop Size you want to set Horizontal Virtual Size to 4. Now click on Back. Make sure Desktop Cube and Rotate Cube are ticked and Wobbly Windows and Snapping Windows are not ticked. With Rotate Cube (click on it) set zoom to something like 0.7.
To rotate the cube hold down Ctrl and Alt and press the left or right arrow, or you can hold Ctrl and Alt and hold down the left mouse button and move the mouse.

---

