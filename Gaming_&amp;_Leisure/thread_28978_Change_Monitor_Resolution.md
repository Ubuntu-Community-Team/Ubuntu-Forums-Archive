---
title: "Change Monitor Resolution"
date: 2005-04-22
forum: Gaming &amp; Leisure
---

### Post by impman89 on 2005-04-22
Is there a way to change the resolution of the monitor when a certain application is run? For example, I want to play the game America's Army at 800*600, while my desktop is 1280*1024.

Now instead of making the whole monitor 800*600, it just shows an 800*600 box within my 1280*1024 screen.

How do i get it to change monitor modes instead of making a sized box with a black border??

---

### Post by jdodson on 2005-04-22
[QUOTE=impman89]Is there a way to change the resolution of the monitor when a certain application is run? For example, I want to play the game America's Army at 800*600, while my desktop is 1280*1024.

Now instead of making the whole monitor 800*600, it just shows an 800*600 box within my 1280*1024 screen.

How do i get it to change monitor modes instead of making a sized box with a black border??[/QUOTE]

is there an "options" or "video" or "settings" selection in the menu.  i would traverse the menu options till i found the setting.  i would imagine it is there somewhere though i have not played americas army.

---

### Post by impman89 on 2005-04-22
thats the point. There is an option, but if i change resolution it doesnt change the monitor mode, it just makes a box within my current mode that is the size i specified. What i want it to do is resize the screen to the specified resolution.

---

### Post by Cimmerian on 2005-04-23
If you run xrandr, you should get a list of available resolutions. If you run xrandr -s <number>, where <number> is the number listed in the first column, you will change your resolution. I guess you would get the same result going to "System->Preferences->Screen Resolution".

Not sure if this is what you want, as I noticed you wanted it to happen when a certain application was run. Maybe you could make a script of some sorts, that would change your resolution and launch AA, then restore your original resolution when the game exits. It's strange that the game does not deal with this properly. 

Hope this helps. 

C

---

### Post by heimo on 2005-04-23
Check that you have 
Load    "extmod"
in your xorg.conf Module section. It loads bunch of modules and if I remember correctly, also the one that allows resolution change "on demand". Can't remember the module name, though.

That's usually in the configfile. Then all you should have to do is change the resolution in the program / game - if it uses fullscreen mode and different resolution, resolution should change automaticly.

---

