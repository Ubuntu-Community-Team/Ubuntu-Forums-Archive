---
title: "No Trashcan on desktop after hardware upgrade"
date: 2010-08-03
forum: Desktop Environments
---

### Post by mister_p_1998 on 2010-08-03
Hi guys, a wierd one here, I finally upgraded my P4 3ghz to a dual core and replaced the onboard Intel video with a nice new Nvidia, all fine except my trashcan icon has vanished from the desktop, its enabled in gconf-editor, Ive tried disabling it, re-booting etc, but it wont come back! Has anyone else had this problem?
Steve

---

### Post by Tamlynmac on 2010-08-03
Just a few quick questions. Which you've probably already tried, but just in case.

1. Have you right clicked on the panel and selected "Add to Panel". From the list select "Trash". That should add the trash icon back to panel.
2. Are you trying to get the trash icon on the actual desktop or in the panel? If your trying to get it on the desktop, drag the trash icon from the panel to the desktop. Or right click on the desktop and select create launcher.

If it doesn't show up on the desktop check to see if it's turned on in the gconf-editor for both:
Nautilus/desktop/trash_icon_visible
Nautilus/preferences/show_desktop

3. If your trying to put it on the desktop (not the panel), do you have any other icons on the desktop and are they showing up? To confirm that the desktop is displaying icons drag a different icon to the desktop and confirm that the icon is visible on the desktop.

Good Luck

---

### Post by mister_p_1998 on 2010-08-04
Just a few quick questions. Which you've probably already tried, but just in case.

1. Have you right clicked on the panel and selected "Add to Panel". From the list select "Trash". That should add the trash icon back to panel.


Its still in the panel, just not on the desktop..

If it doesn't show up on the desktop check to see if it's turned on in the gconf-editor for both:

First thing I did..

3. If your trying to put it on the desktop (not the panel), do you have any other icons on the desktop and are they showing up? 
Yep theres lots of other icons..

---

### Post by Tamlynmac on 2010-08-04
Stretching my memory... ;)

I remember a problem with the applet in the panel disappearing and  necessitating that the applet be replace and a reboot required  (restarting the X server). Perhaps that also applies to the desktop. I  never used a desktop trash applet icon.

I recalling having a problem on a number of systems not showing certain  icons on the desktop in 8.04. The issues were directly related to Compiz  and one or two icon themes. After turning off visual effects and/or changing the icon theme, the problem was eliminated.

One additional issue I recall with the trash applet was when using AWN in 8.04. I  believe there was a patch for AWN. I've never used AWN so can't help  much.

Hopefully, others have some feedback that may help. It's been a while since I used 8.04. :D

Sorry I couldn't be more help.
Good Luck
 Mac

* One quick question, have you considered upgraded to 9.04? It's been my experience that the 9.04 upgrade eliminated many of the 8.04 problems and I haven't found a system that wouldn't make the upgrade (including my Dell Mini that ran the 8.04 Dell remix). I experienced more problems with 8.1 than with 8.04 and 9.04 was a big improvement. I'm still using 9.04 on most of our home systems as 9.1 and 10.04 tested poorly on a number of our systems. Perhaps, use a live USB stick or CD to test your system for compatibility and of course if you have a spare HDD or petition on your primary, you could install 9.04 and run a complete functionality test. Just a thought.

Most all the individuals I know who use Ubuntu, fall back on 9.04 should they have problems with 9.1 or 10.04. It's an extremely stable platform and does exceptionally well with older systems.

Sorry I couldn't be more help.
Good Luck
Mac

---

### Post by Ginsu543 on 2010-08-06
You can easily add a Trashcan to the Desktop by using [_Ubuntu Tweak_](http://ubuntu-tweak.com/). Just go to "Desktop Icon Settings" and click the "Show 'Trash' icon on desktop" option.

---

### Post by mister_p_1998 on 2010-08-07
Sorted it!
Right button on Desktop and chose 'Keep Aligned' and the trashcan popped back onto the desktop, must have moved out of sight when I changed the video card.

---

### Post by Ginsu543 on 2010-08-07
Excellent! You can now mark this thread [SOLVED]. :)

---

