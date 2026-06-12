---
title: "gnome 3 problems"
date: 2012-08-11
forum: Desktop Environments
---

### Post by blackmail on 2012-08-11
So I installed Ubuntu 12.04 and after that installed the necessary packages to be able to revert back to gnome classic, without the unity thing. so when you start the computer with the gnome classic interface, the system option is gone, but thet is not a problem, nonetheless the bar at the bottom of the screen is a problem. i have never used it in the past and it was as simple as right click and then remove or delete, something like that, and it went away. now if i right click no menu apears... this is rather bad, and i also tried killing it with xkill, but then for a second there it disapears along with the upper bar containing the menu items. this happens for a second or so after which both of them reapear, how could i remove the bottom bar? and if i make a wideo fullscreen on let's say youtube, the bottom and the top bars are visible, what could be the problem?

---

### Post by cortman on 2012-08-11
> **blackmail said:**
> So I installed Ubuntu 12.04 and after that installed the necessary packages to be able to revert back to gnome classic, without the unity thing. so when you start the computer with the gnome classic interface, the system option is gone, but thet is not a problem, nonetheless the bar at the bottom of the screen is a problem. i have never used it in the past and it was as simple as right click and then remove or delete, something like that, and it went away. now if i right click no menu apears... this is rather bad, and i also tried killing it with xkill, but then for a second there it disapears along with the upper bar containing the menu items. this happens for a second or so after which both of them reapear, how could i remove the bottom bar? and if i make a wideo fullscreen on let's say youtube, the bottom and the top bars are visible, what could be the problem?

Alt+right click.

---

### Post by blackmail on 2012-08-11
tried that before and it did not work, but i tried it again and it still doesn't work, no menu is shown, be it the lower or upper bar.

---

### Post by cortman on 2012-08-11
Try

```
sudo apt-get purge gnome-panel
sudo apt-get install gnome-panel
```

You should do this from Unity.

---

### Post by kansasnoob on 2012-08-12
> **cortman said:**
> Alt+right click.

That's for gnome classic (no effects) only, if the OP is using standard "gnome classic" then it's Alt + Super Key + right-click (the super key is typically the one with the windows logo).

@ blackmail, you might find some other helpful hints here:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

But it's written for classic (no effects) which uses the Metacity window manager, whereas the standard classic session uses Compiz.

---

### Post by blackmail on 2012-08-12
Thank you all for the quick answers, after reading your answers, i logged out from this session, and logged back in to the gnome without effects session, and i oculd change stuff around, so i did the changes that way, and they where still there when i logged back in to the Gnome and COmpiz session.

thnx again!

---

