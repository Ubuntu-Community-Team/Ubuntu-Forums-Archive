---
title: "Gimp 2.6.3 &quot;main&quot; window always in the back?"
date: 2009-02-08
forum: General Help
---

### Post by cub on 2009-02-08
I upgraded to Ubuntu 8.10 some time ago and got Gimp 2.6.3 with the installation. For some reason when I open a picture I'd like to work with the window with the picture is always behind the Toolbox- and Layers-window. This is very annoying since I got a laptop with small screen and I'd like to choose which window I got on top, like before my upgrade.

I've tried to find any settings for this and also searched a lot but haven't found anything so far. Anyone recognize the problem and know a solution?

---

### Post by utnubuuser on 2009-02-08
Hi - lol, I found the same issue, using gimp on a little 12.1 inch screen.
I got onto the gimp forum and asked, and apparently it's a new feature for 2.6.x.  
I guess most people who do a lot of work in gimp, (and the developers), have either wide-screens, or have more than one screen, so the toolbars etc get moved to the secondary screen.  It's built in now, and it's not selectable.  --bit of a bummer for those of us with small screens.

---

### Post by igknighted on 2009-02-08
The gimp toolbox and layers are no longer their own windows, they are more panels that are docked there.  I forget the exact way it works, but they aren't designed to act on their own.

However, if you turn on compiz, it doesn't understand the docked windows, so it displays them on their own and they often drop to the background (annoying for me... good for you?)

---

### Post by cub on 2009-02-09
Nice "feature" :(

I can't turn on Compiz since the graphic card in my old laptop is too crappy.

I guess I have to downgrade Gimp somehow then. My first setback in the Ubuntu world.

---

### Post by lakelovers on 2009-02-09
Here's the way to move the main window to "always in front" (on V 2.6.3). On the tool bar in the main window go Edit> Preferences> Input Devices> Window Management. In the Window Management section you'll find "Window Manager Hints." On both the Tool Box hint and the Dock hints, select "Nomal Window."

---

### Post by utnubuuser on 2009-02-09
> **lakelovers said:**
> Here's the way to move the main window to "always in front" (on V 2.6.3). On the tool bar in the main window go Edit> Preferences> Input Devices> Window Management. In the Window Management section you'll find "Window Manager Hints." On both the Tool Box hint and the Dock hints, select "Nomal Window."

Thanks Lakelovers!!!  --

---

### Post by igknighted on 2009-02-09
> **cub said:**
> Nice "feature" :(

I can't turn on Compiz since the graphic card in my old laptop is too crappy.

I guess I have to downgrade Gimp somehow then. My first setback in the Ubuntu world.

I guess you can't please everyone... The biggest complaint about GIMP has always been that the toolbox and layers were handled the way you want them, and not what they have switched to.  The 2.6 series has been really disappointing feature-wise anyhow, so if the 2.4 interface works better for you, then you really aren't missing much.

---

### Post by cub on 2009-02-11
> **lakelovers said:**
> Here's the way to move the main window to "always in front" (on V 2.6.3). On the tool bar in the main window go Edit> Preferences> Input Devices> Window Management. In the Window Management section you'll find "Window Manager Hints." On both the Tool Box hint and the Dock hints, select "Nomal Window."
Yes! Thanks a lot!

---

### Post by cub on 2009-02-11
> **igknighted said:**
> I guess you can't please everyone... The biggest complaint about GIMP has always been that the toolbox and layers were handled the way you want them, and not what they have switched to.  The 2.6 series has been really disappointing feature-wise anyhow, so if the 2.4 interface works better for you, then you really aren't missing much.
What I mostly was against was that there was no way to choose between the different way to handle the windows.

But apparently there was, so all is good. They can please everyone. :D

---

### Post by cb951303 on 2009-02-11
May I suggest another way (a better one in my opinion)

Use the GIMP as is, but make your middle mouse button to roll up and down the windows. This way in full screen, you can roll up the toolboxes and work as you like. and then you can bring them with a click of middle button.
I would like to use scroll wheel instead of middle button but unfortunately gnome doesn't allow it.

Here is a screenshot of what I mean

---

### Post by cub on 2009-02-12
> **cb951303 said:**
> May I suggest another way (a better one in my opinion)

Use the GIMP as is, but make your middle mouse button to roll up and down the windows. This way in full screen, you can roll up the toolboxes and work as you like. and then you can bring them with a click of middle button.
That sounds nice. But how do I configure that? I didn't find anything in System-Preferences-Mouse or in the GIMP Preferences.

---

### Post by cb951303 on 2009-02-12
> **cub said:**
> That sounds nice. But how do I configure that? I didn't find anything in System-Preferences-Mouse or in the GIMP Preferences.

ah sorry about that. 
run "Configuration Editor" go to "apps > metacity > general" and change action_middle_click_titlebar's value to "toggle_shade" (without double quotes).

---

### Post by cub on 2009-02-15
Yay, even better! Solution 2 is a keeper. Thanks!

---

### Post by cb951303 on 2009-02-15
> **cub said:**
> Yay, even better! Solution 2 is a keeper. Thanks!

no problem. it would be even better if gnome lets us toggle_shade with scroll wheel. XFCE allows it and it's much better than clicking the middle button.

---

### Post by boxrec on 2010-02-09
> **cb951303 said:**
> ah sorry about that. 
run "Configuration Editor" go to "apps > metacity > general" and change action_middle_click_titlebar's value to "toggle_shade" (without double quotes).

Brilliant, Brilliant, Brilliant
:KS :KS :KS :KS :KS :KS :KS

---

