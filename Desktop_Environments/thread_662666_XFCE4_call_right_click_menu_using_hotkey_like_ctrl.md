---
title: "XFCE4 call right click menu using hotkey like ctrl^m"
date: 2008-01-09
forum: Desktop Environments
---

### Post by nutts4life on 2008-01-09
Hi there,

I have turned off the right click menu on the display manager. But i still want access to the right click menu using a hotkey.

Can the right click menu be called as an excecutable by a hotkey?

bit random i know, but i'm looking to lock down my PC so that the user can only use icons on a panel, 
but more experienced users have the ability to manage the computer by opening the menu using a hotkey like ctrl^m.

I'd rather not install mouseemu,

any help would be great.

thanks, :)

---

### Post by santiagoward2000 on 2008-01-09
> **nutts4life said:**
> Hi there,

I have turned off the right click menu on the display manager. But i still want access to the right click menu using a hotkey.

Can the right click menu be called as an excecutable by a hotkey?

bit random i know, but i'm looking to lock down my PC so that the user can only use icons on a panel, 
but more experienced users have the ability to manage the computer by opening the menu using a hotkey like ctrl^m.

I'd rather not install mouseemu,

any help would be great.

thanks, :)

Hi!
I have an idea, but you'll have to enable the right click menu on the display manager. Once it's enabled, go to **Applications/Settings/Keyboard Settings** and under shortcuts, add a new one with this command:
```
xfdesktop --menu
```
If the right click menu is disabled, you'll get the **"Create Launcher, Create Folder," etc** menu.
Cheers!

---

### Post by nutts4life on 2008-01-09
Thanks very much,

I tried that and it works. BUT only with right click menu turned on in the desktop manager.
That means i can still access it by right clicking as well as my shortcut.

What i really want is that this setting is overridden if right click menu is turned off in the desktop menu.

And i guess this is where it gets a little impossible as i imagine the xfdesktop executable checks this setting before the menu is displayed.

So lets leave that idea for now.

Really what i'd like to do is completely shutdown the concept of right click functionality in XFCE4.
Any ideas on how i could catch a right click mouse button before it is sent to the windows manager. OR even fool the ubuntu into thinking that i only have a left button mouse!!!!

Any ideas would be great, thanks.

O :)

---

### Post by nutts4life on 2008-01-10
bummpy bumdiddy bumper

---

