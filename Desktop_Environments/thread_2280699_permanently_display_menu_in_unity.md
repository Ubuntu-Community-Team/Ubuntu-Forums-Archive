---
title: "permanently display menu in unity"
date: 2015-06-01
forum: Desktop Environments
---

### Post by chopra on 2015-06-01
I had been giving Unity a try, but one thing I can't stand is that menu items at the top of a terminal shell, or other application, dissapear unless you mouse over them.  I found this webpage:

[http://askubuntu.com/questions/25785/can-auto-hide-for-the-application-menu-be-turned-off-in-unity](http://askubuntu.com/questions/25785/can-auto-hide-for-the-application-menu-be-turned-off-in-unity)

which gave the command:

gsettings set com.canonical.Unity always-show-menus true

to turn on the feature, and the command:

gsettings set com.canonical.Unity always-show-menus false

to turn it off.  It worked, but now, after having performed the first command, the menu items show up, but cannot be accessed by the mouse.  It's as if they're just words printed on the bar above the command shell, which the mouse buttons are ovblivious to.  The same situation applies to my web browser.  I used the second command to turn it back off.  Now, the appearance is the same as before, (menu items only appear when moused over), but they still can't be activated by the mouse.  This affects my main account, and also a secondary account I had created.

the problem only affects the unity desktop; the gnome classical compiz desktop is unaffected.  So, for now, Unity is not an option for me.  Any ideas?

Chopra

---

### Post by Copper Bezel on 2015-06-02
Hmm. No. If you logged in as a separate account (even the guest account,) that account doesn't know anything about *your* user's dconf and gconf settings, which reside respectively as a binary flat file and a directory tree of xmls in your user directory. I don't think your tweaking is what broke the menus, but I don't know what else might have. = [

---

### Post by chopra on 2015-06-04
Well, if that's the case, it would appear to be an issue with Unity itself on my laptop, then.  Now that I think of it, I never did actually try to use the menu items before making the change.  Maybe incompatability with something else I downloaded.  I'll have to investigate further...

---

### Post by Copper Bezel on 2015-06-04
Do the menus open when you hit Alt+F10?

---

### Post by chopra on 2015-06-06
> **Copper Bezel said:**
> Do the menus open when you hit Alt+F10?

Yes, it does.  Strange, but after further experimentation, it seems that the mouse is able to activate the menus some of the time, but not always.  Sometimes, I have to move the pointer to the menu item and nudge it until it's in exactly the right place.  Other times, that doesn't work, but I can highlight one menu item with the pointer, and then move to the left or right to a different item.

So it seems that Unity is very picky about the mouse.  This can't be normal behavior.  It will work for a while, and then I go to a different window, and come back, and I have to fidget with things again until I am able to activate a drop-down menu item.  Then all of the items work fine.

Chopra

---

