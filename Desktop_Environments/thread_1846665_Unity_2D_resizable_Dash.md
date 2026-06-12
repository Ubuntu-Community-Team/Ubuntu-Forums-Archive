---
title: "Unity 2D resizable Dash?"
date: 2011-09-19
forum: Desktop Environments
---

### Post by galacticaboy on 2011-09-19
How can I make the Dash in Unity 2D resizable or make it smaller and larger? I know it can be done, I have done it once, I just do not remember how I did it.

---

### Post by Blasphemist on 2011-09-19
You install ccsm and adjust the size by clicking on the unity plugin button.

---

### Post by Krytarik on 2011-09-19
> **Blasphemist said:**
> You install ccsm and adjust the size by clicking on the unity plugin button.
The Ubuntu Unity Plugin settings in CCSM don't affect Unity 2D at all! ;-)

It is possible to change the size of the Dash in the original Unity, as described at the link below, but I don't think that it affects Unity 2D, too:

[http://askubuntu.com/questions/59837/how-to-get-the-unity-dash-overlayed-not-maximized-by-default](http://askubuntu.com/questions/59837/how-to-get-the-unity-dash-overlayed-not-maximized-by-default)

Greetings.

---

### Post by galacticaboy on 2011-09-19
> **Krytarik said:**
> The Ubuntu Unity Plugin settings in CCSM don't affect Unity 2D at all! ;-)

It is possible to change the size of the Dash in the original Unity, as described at the link below, but I don't think that it affects Unity 2D, too:

[http://askubuntu.com/questions/59837/how-to-get-the-unity-dash-overlayed-not-maximized-by-default](http://askubuntu.com/questions/59837/how-to-get-the-unity-dash-overlayed-not-maximized-by-default)

Greetings.

I just figured that out! haha Thanks

---

### Post by Blasphemist on 2011-09-19
In order to ensure I don't get this wrong the next time, does gconf-editor work for this or is there some other solution?

---

### Post by IWantFroyo on 2011-09-19
> **Blasphemist said:**
> In order to ensure I don't get this wrong the next time, does gconf-editor work for this or is there some other solution?

Probably not. I doubt gconf-editor was modified to work with Unity, and the Gnome guys wouldn't have done it.
It probably doesn't go past some of the aspects of the panel.

---

### Post by Blasphemist on 2011-09-19
Hmmmm, you'd think there would be a way especially with unity 2D being carried forward.

---

### Post by arzali on 2011-09-20
if you want a customizable 2d-launcher why not try dockbarx?

It has most of the unity launcher features and more.
you can resize it, theme it, put it on another side of the display ...
see in action with ocelot 
[[IMG]http://uppix.net/7/e/d/2063c842871cd845058d3425c2377tt.jpg[/IMG]]("http://uppix.net/7/e/d/2063c842871cd845058d3425c2377.png")


Info dockbarx: [http://gnome-look.org/content/show.php/DockbarX?content=101604](http://gnome-look.org/content/show.php/DockbarX?content=101604)
unity theme for dbx: [http://bigrza.deviantart.com/gallery/#/d39veh3](http://bigrza.deviantart.com/gallery/#/d39veh3)

---

### Post by Krytarik on 2011-09-20
> **arzali said:**
> if you want a customizable 2d-launcher why not try dockbarx?
It's about the Dash, not the Launcher.

> **arzali said:**
> see in action with ocelot 
[[IMG]http://uppix.net/7/e/d/2063c842871cd845058d3425c2377tt.jpg[/IMG]]("http://uppix.net/7/e/d/2063c842871cd845058d3425c2377.png")
[]("http://bigrza.deviantart.com/gallery/#/d39veh3")
This is obviously no screenshot of DockbarX, but of Unity.

---

### Post by arzali on 2011-09-20
> **Krytarik said:**
> It's about the Dash, not the Launcher.

oops i  thout the launcher was also called dash :oops:

> **Krytarik said:**
> This is obviously no screenshot of DockbarX, but of Unity.
 
thats a joke, right? If not than i think i did a good job copying the unity launcher :)

---

### Post by mcduck on 2011-09-20
> **IWantFroyo said:**
> Probably not. I doubt gconf-editor was modified to work with Unity, and the Gnome guys wouldn't have done it.
It probably doesn't go past some of the aspects of the panel.

There's nothing in gconf-editor that would require it to be modified to handle anything. ;) If a program uses gconf to store it's settings, then gconf-editor will handle it. Simple as that. :D

Anyway, the Dash settings are stored in dconf/GSettings, not gconf, so dconf-editor is the tool to use here. It's included in the dconf-tools -package.

---

### Post by philinux on 2011-09-20
The icons on the launcher can be resized 32 is the minimum. Dash however cannot it is hard coded. There is a bug report asking for it to be customised.

 [http://ubuntuforums.org/showthread.php?t=1844109](http://ubuntuforums.org/showthread.php?t=1844109)

---

### Post by Krytarik on 2011-09-20
> **philinux said:**
> The icons on the launcher can be resized 32 is the minimum. Dash however cannot it is hard coded. There is a bug report asking for it to be customised.

 [http://ubuntuforums.org/showthread.php?t=1844109](http://ubuntuforums.org/showthread.php?t=1844109)
This - again - is about the original Unity, not Unity 2D. And about the icons, not the frame size of the Dash.

However, if someone wants to resize the Launcher icons in Unity 2D, it can possibly be done by following this guide:

[http://bhou.wordpress.com/2011/05/06/change-the-icon-size-in-unity-2d-launcher/](http://bhou.wordpress.com/2011/05/06/change-the-icon-size-in-unity-2d-launcher/)

---

### Post by Krytarik on 2011-09-20
> **arzali said:**
> thats a joke, right? If not than i think i did a good job copying the unity launcher :)
Does DockbarX also feature a button to invoke the Dash now? And yes, just noticed that the launcher doesn't expand to the bottom of the screen, which I guess is still impossible with the new versions of Unity. And yeah, the icons and the general look of the launcher pretty well resemble those of Unity. :)

---

