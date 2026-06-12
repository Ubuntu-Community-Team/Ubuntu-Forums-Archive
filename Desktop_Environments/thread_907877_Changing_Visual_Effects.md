---
title: "Changing Visual Effects"
date: 2008-09-01
forum: Desktop Environments
---

### Post by MaindotC on 2008-09-01
When you change the visual effects setting from None to Normal or Extra, what exactly is happening?  For example, almost all of the windows close and then reopen, sometimes I lose Firefox and have to restart it (which is not really a concern of mine), the screen flickers...stuff like that.

Is it like a condensed version of restarting the X server - something like that?

---

### Post by jay.squid on 2008-09-02
visual effects animates your windows etc. makes it look a lot more polished (when you close a box it folds and fades instead of just disappearing) try dragging a window around the screen when visuals are turned fully up and you'll see! plus theres addons to make your desktop look awesome!!!

---

### Post by MaindotC on 2008-09-02
I know what visual effects are - I'm trying to understand why there seems to be some discombobulation when switching between None and Normal or Extra.  I was just curious if it does the same thing as restarting the X server but in a kind of tiny format.

---

### Post by Goombie on 2008-09-02
I don't know if it restarts the X-Server; it restarts the Window Manager, which is the program that takes care of drawing, moving around, and other aspects of managing your Windows. The Compiz Window Manager (which you turn on with the visual effects) provides more effects when you move your windows around, animations when the windows are opened/closed/minimized, etc. 
If you haven't already, I'd recommend installing the packages *simple-ccsm* and *compizconfig-settings-manager* using the method of your choice. Once installed, you can find them in System>Preferences menu ("Advanced Desktop Effects Settings" and "Simple Compiz Config Settings Manager"). They are both configuration programs that let you change how Compiz works; that is, what animations are used, what plugins you can use, shortcut keys, and so on. Once you've installed the packages, you'll also see an extra option for visual effects: custom, where you can fine-tune the effects using the programs I mentioned.

---

### Post by lunkupe on 2008-09-03
I think you may have installation issues and so I guess you should reinstall the OS especially if you are losing windows all of a sudden or some just minimize if this does not help then your hardware is being overstrained and thus just disable the effects but this only happends to old hardware and not new ones.

---

### Post by tuxxy on 2008-09-03
The discombobulation lol is when the settings for compiz are being changed and also the emerald window manager being enabled when you select extra effects.

To manually edit what effects you would like, install the package **ccsm**, and to edit your window themes or apply new themes download **emerald** both are available in the repos.

---

### Post by Goombie on 2008-09-03
It should also be noted that Compiz works fine with the default Window decorator for Hardy, GTK Window Decorator. Emerald is nice, but I don't use it because I found it kind of confusing.

---

