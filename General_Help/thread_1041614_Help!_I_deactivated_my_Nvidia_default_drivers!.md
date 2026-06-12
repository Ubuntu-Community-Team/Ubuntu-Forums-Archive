---
title: "Help! I deactivated my Nvidia default drivers!"
date: 2009-01-16
forum: General Help
---

### Post by Ericthelad168 on 2009-01-16
I deactivated the Nvidia drivers, and now when I restart my computer, it just shows up in random colors and blocks, and I am unable to do anything at all.  
Is there a way for me to re-activate my drivers using command line?

Help would be greatly appreciated for my stupidity!

---

### Post by dcstar on 2009-01-16
> **Ericthelad168 said:**
> I deactivated the Nvidia drivers, and now when I restart my computer, it just shows up in random colors and blocks, and I am unable to do anything at all.  
Is there a way for me to re-activate my drivers using command line?

Help would be greatly appreciated for my stupidity!

There are detailed instructions in the forums for editing the /etc/X11/xorg.conf file (which you will probably have to do to get going again).

Just search them out.

---

### Post by Ericthelad168 on 2009-01-16
Thank you for your response, I wasn't sure if that is where the problem was.  I am very new to Ubuntu, and have not had a chance to get a grasp of everything yet.  Sadly, I have to tinker with things (No text appears in dropdown menus in OpenOffice, and was trying to install older drivers, which from reading forums was a good fix, and it said I had newer ones on there, so I tried to deactivate the new ones, then just install the new ones, but it didn't work so well, and without thinking, I turned my machine off.)

---

### Post by 2hot6ft2 on 2009-01-16
> **Ericthelad168 said:**
> Thank you for your response, I wasn't sure if that is where the problem was.  I am very new to Ubuntu, and have not had a chance to get a grasp of everything yet.  Sadly, I have to tinker with things (No text appears in dropdown menus in OpenOffice, and was trying to install older drivers, which from reading forums was a good fix, and it said I had newer ones on there, so I tried to deactivate the new ones, then just install the new ones, but it didn't work so well, and without thinking, I turned my machine off.)
For the Open Office menus
[http://ubuntuforums.org/showthread.php?t=1036129&highlight=menus+OpenOffice](http://ubuntuforums.org/showthread.php?t=1036129&highlight=menus+OpenOffice)
and here
[http://ubuntuforums.org/showthread.php?t=964052&highlight=menus+OpenOffice](http://ubuntuforums.org/showthread.php?t=964052&highlight=menus+OpenOffice)
turning desktop effects off or on seems to work for some.

For the graphics try rebooting and choosing the recovery mode then at the menu choose the last one xfix then when it finishes choose the first one = boot normally.

---

### Post by 2hot6ft2 on 2009-01-16
Here's the one I was looking for to fix the Open Office Menus.
> **luminol said:**
> What did it for me was going to System --> Preferences --> Appearance --> Fonts and clicking Subpixel Smoothing. Worked fine after that.

---

