---
title: "Panels lost after increasing screen resolution"
date: 2010-05-18
forum: Desktop Environments
---

### Post by AntoniusUno on 2010-05-18
I have a weird problem that after increasing the screen resolution from 1024x786 (4:3) to 1280x900 something (also 4:3) that both top and bottom panels have disappeared. I am not familiar with the keyboard shortcuts to much but managed to get a terminal running so I should be able to do some command line stuff but as I am not too familiar where to edit perhaps someone can give me some pointers.

I guess first step is to restore the resolution to the original. Anyone any ideas?

---

### Post by igsen on 2010-05-18
Can you not access system>preferences>screen resolution and from there go back to your default?

---

### Post by portentum on 2010-05-18
> **igsen said:**
> Can you not access system>preferences>screen resolution and from there go back to your default?
No, because *their panels are gone.* 

[QUOTE=AntoniusUno]I have a weird problem that after increasing the screen resolution from 1024x786 (4:3) to 1280x900 something (also 4:3) that both top and bottom panels have disappeared. I am not familiar with the keyboard shortcuts to much but managed to get a terminal running so I should be able to do some command line stuff but as I am not too familiar where to edit perhaps someone can give me some pointers.

I guess first step is to restore the resolution to the original. Anyone any ideas?[/quote]
You can run gnome-control-center in the terminal, which should give you access to the config options you need, and will likely allow you to restore the panels without changing the resolution.

Hope this helps.

---

### Post by AntoniusUno on 2010-05-20
I just found out that if I undock the laptop from the docking station the panels are there but when docked and on an external monitor the panels disappear. If I open the system monitor tool and kill gnome-panel, the panel appears shortly on the bottom of the screen and then is killed and restarts itself. During the brief moment that the panel appears, I am able to click and manipulate with it as if the panels were normally there. 
So this makes me think that though the monitor is correctly detected, the screen size is not correctly set (larger than the monitor. The mouse disappears at the bottom of the screen as if there is more space than displayed. 

Does anyone know how this can be solved? I would like to keep switching between the docking station and laptop use.

---

### Post by portentum on 2010-05-20
If you check the resolution both with it docked and not, does it say it's the same?

When docked are you using an external monitor? If so, do you know what resolutions it supports?

Also, could you share the model of your laptop?

If the problem turns out to be that an external monitor on the docking station doesn't like the resolution, [this]("http://www.doyouubuntu.com/wordpress/?p=8&lang=en") could be of some help. It's old, but it's a place to start.

---

