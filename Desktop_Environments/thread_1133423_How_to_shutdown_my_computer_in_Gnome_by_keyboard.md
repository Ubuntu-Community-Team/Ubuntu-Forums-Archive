---
title: "How to shutdown my computer in Gnome by keyboard?"
date: 2009-04-22
forum: Desktop Environments
---

### Post by yookoala on 2009-04-22
I used to do this:
[LIST=1]
[*]Alt-F1 to go to menu.
[*]Use Left/Right/Up/Down arrow to go to Shutdown. Press enter.
[*]The pop-up can be operated with keyboard. I select Shutdown and press enter
[/LIST]

Now, Shutdown is separated from the menu. I cannot do this anymore.

---

### Post by StuartN on 2009-04-23
> **yookoala said:**
> Now, Shutdown is separated from the menu. I cannot do this anymore.

Add shutdown to the menu by adding a new menu item to run the following command:

gnome-session-save --shutdown-dialog

---

### Post by yookoala on 2009-04-23
I know I can add menu item.
I also can use Gnome Do (with plugin) to shutdown.
I can even go to terminal by Alt F1-F6, where I can use "shutdown -h now" to shutdown.

But I'm talking about default installation.
Is there any way to access the shutdown menu by keyboard?

---

### Post by Darkshade on 2009-04-23
Ctrl+Alt+Delete. Then Alt+S or click Shut Down

---

### Post by yookoala on 2009-04-25
OK. But again that is not GUI.

---

### Post by arekmenner on 2009-06-24
Hmm... as far as I know, there are precious few ways to access the new Gnome logout menu from the keyboard. Maybe someone can prove me wrong. Basically what I'm saying can be condensed down to this:

*There's a button with my name and a little power button near the upper right hand corner. Is there a good way to access the associated dropdown menu with the keyboard?*

I guess that new little dropdown menu also has some integration with pidgin. Honestly, I'm not familiar enough with it to have much use for it aside from locking screen and whatnot, and you can use Ctrl+Alt+Del to get a shutdown menu, but as far as accessibility rules go, shouldn't it be reachable by keyboard?

At the moment, the best (crappy) workaround I can get is using Ctrl+Alt+Tab to focus on the top edge panel and then tab over to my name and then log out or guest session. It doesn't even highlight in any way when I tab over to it.

If anybody knows if there is a better way, it would be nice to know. Otherwise it might be time to file a bug.

---

### Post by Chemical Imbalance on 2009-06-24
Btw, does anyone know why the shutdown options were moved out of the main menu?

Bad decision IMO.  What happens to Grandma when she can't shut her computer down?  Know what I mean?

---

### Post by ratcheer on 2009-06-24
```
sudo init 0
```

Or, is this not what you mean?

Tim

---

### Post by arekmenner on 2009-06-24
Hahah, no, that's not what we mean.

I mean, yeah, there are myriad ways to shut down with the keyboard (reboot, shutdown, Ctrl+Alt+Del, etc, etc). We're just looking for "The Right Way", or more appropriately, a way to reach that silly login/shutdown dropdown menu with the keyboard.

I can't speak for everyone, but my motivations are firstly idle curiosity and then accessibility.

---

