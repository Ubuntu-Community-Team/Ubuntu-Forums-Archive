---
title: "WoW, wine, and KDE = no alt click?"
date: 2006-12-13
forum: Gaming &amp; Leisure
---

### Post by glave on 2006-12-13
Ok, for some reason, something is grabbing my alt key while I'm trying to play WoW. I cannot alt click anything to put in trade windows, auction house, nothing. 

I've looked high and low, and saw other posts mentioning this with other apps in wine (photoshop), but I've seen no resolutions other than some tweaks in gnome (and I'm in KDE!).


Any direction to go in?

---

### Post by hikaricore on 2006-12-13
You could try running wow on it's on X screen, as detailed in tip two of z00s' post here:

[http://ubuntuforums.org/showthread.php?t=303509&highlight=wow](http://ubuntuforums.org/showthread.php?t=303509&highlight=wow)

This way nothing else will be running on the X session wow is using that could possibly affect keybindings but wow.

---

### Post by chadk on 2006-12-13
alt-click is default for moving windows in gnome or something I think because mine does it as well.  Even if I put wow on it's own x session using the instructions on the isntall how-to.  It's annoying because several add-ons use alt-click.

---

### Post by hikaricore on 2006-12-13
Gnome doesn't load if you launch an xsession this way.  Your answer lies elsewhere.

---

### Post by Afoot on 2006-12-13
This is because of kwin (KDE's window manager). You can easily change this behaviour by going into KDE's control center (or whatever it's called) and you are able to change it there. I can't give you exact instructions - I'm using GNOME at the moment - but you should be able to find the keyboard settings somewhere around there.

In GNOME, you can just go to System -> Settings -> Windows.

---

### Post by glave on 2006-12-13
I figured it out. Turns out it was a combination of how I had wow configured and KDE's window behavior. 

Short Answer:
kcontrol-> Desktop-> Window Behavior-> Window Actions-> Modifier key


Long Answer:
I run wow off of my ntfs partition, because I still sometimes boot into WinXP and play from there as well. In WinXP I'm using both of my monitors, and I have wow set to maximized full screen, but in *windowed mode*, so I can move my mouse over to the other monitor. Since I'm using the same wow install in kubuntu, it is still set to windowed mode, even though I'm running full screen, so when I'd press alt, kde was trying to treat it as a window.

Tada!

---

### Post by Afoot on 2006-12-15
> **glave said:**
> 
Long Answer:
I run wow off of my ntfs partition, because I still sometimes boot into WinXP and play from there as well. In WinXP I'm using both of my monitors, and I have wow set to maximized full screen, but in *windowed mode*, so I can move my mouse over to the other monitor. Since I'm using the same wow install in kubuntu, it is still set to windowed mode, even though I'm running full screen, so when I'd press alt, kde was trying to treat it as a window.

Try unchecking "Windowed Mode" - KDE (kwin to be correct) will still behave the same.

---

