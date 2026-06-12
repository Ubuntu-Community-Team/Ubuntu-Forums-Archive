---
title: "My main panel keeps distorting on startup?"
date: 2011-03-11
forum: Desktop Environments
---

### Post by Throne777 on 2011-03-11
I've been getting this on & off since day 1 of install, & I've only just gotten round to deciding to see if something can be done about it. 
I've attached a screenshot to show the problem (top right of the screen). Loads like that (though how it messes up -i.e. what it looks like- isn't consistent) from startup & stays like it until I restart the computer or whatever. 
Doesn't happen everytime, just quite frequently. I've just put up with it until now, but it's getting kind of annoying.
Thoughts?

If it helps:
Running 10.10 x64
Visual effects are set to normal. Problem occurs in every theme I've used.
Not running any unusual or bizarre things in that panel either. It's just the ones that are there by default.

---

### Post by gordintoronto on 2011-03-11
If you right-click there, can you see a "preferences" option? Open it, and see what preferences it offers.

Or perhaps you just need to right-click, select "add" and add the clock.

---

### Post by Throne777 on 2011-03-12
> **gordintoronto said:**
> If you right-click there, can you see a "preferences" option? Open it, and see what preferences it offers.

Or perhaps you just need to right-click, select "add" and add the clock.

It's not that. It's that they won't display properly, the computer still thinks they're running/there just fine. 
For instance, sometimes the Gnome Do icon is one of the things that disappears/distorts, yet Gnome Do is still running fine (i.e. pressing Super + Space brings it up).
Same can happen with Banshee/Rhythmbox (I make them display an icon in the notification area); the program will minimise to the icon, yet the icon isn't there.

---

### Post by Throne777 on 2011-03-13
OK, so I've taken another screenshot to show that it distorts but the applet is still there (again, top right).
Note also the time/date app works fine, the extra '10' on the end isn't connected to any app. The desktop thinks that area is blank.
& as usual, the 'shutdown/restart/etc' button isn't there on the end.

---

### Post by Krytarik on 2011-03-13
You may try to reset the panels to their defaults, it won't hurt much since you didn't customize them much:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by Throne777 on 2011-03-21
> **Krytarik said:**
> You may try to reset the panels to their defaults, it won't hurt much since you didn't customize them much:
```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

Well that works, wondering if there's any way to stop it happening in the first place, as opposed to sweeping the problem under the rug?

---

### Post by Krytarik on 2011-03-21
> **Throne777 said:**
> Well that works, wondering if there's any way to stop it happening in the first place, as opposed to sweeping the problem under the rug?
Let's wait and see if those issue re-occurs. Locking the items may help.

---

### Post by Throne777 on 2011-03-21
> **Krytarik said:**
> Let's wait and see if those issue re-occurs. Locking the items may help.

Everything has always been locked to panel. 
First restart and the panels are distorted again (and the panels were simply at the default setting).

---

### Post by Krytarik on 2011-03-21
Do you have autologin enabled?
If not, does the screen resolution change when logging in?

---

### Post by Throne777 on 2011-03-21
> **Krytarik said:**
> Do you have autologin enabled?
If not, does the screen resolution change when logging in?

No & nope.
Resolution is 1680 x 1050 (if that helps)

---

### Post by Krytarik on 2011-03-21
Does a simple restart with "killall gnome-panel" also fix its appearance (for the running session)?

---

