---
title: "Click to activate window on Gnome"
date: 2009-08-23
forum: Desktop Environments
---

### Post by KLineD on 2009-08-23
For some time I used OSX Leopard. One feature I did like was the "click to make window active". The reason I like it is that I don't need to find a safe area to click in order to make some window active.

I've tried to get the same in Gnome, but no luck so far. I'm sorry if this has been asked before (I searched the forums, couldn't find anything).

Is there a setting in gconf or a tweak that can enable this type of behavior in Gnome?

Thanks in advance!

---

### Post by ajgreeny on 2009-08-23
I am not certain that I understand fully what you are trying to get to work, or at least, if I do understand, then I already have that behaviour.  Can you explain more please what you want, and what you have happening now.

---

### Post by KLineD on 2009-08-23
Sure!

Let's say I have two windows open on your desktop: nautilus and firefox. Firefox is partially blocking nautilus, that is, you can see part of nautilus' GUI but you are working on firefox.

Then I click on nautilus, and that click landed on nautilus' File submenu. That click brings nautilus to the front, now blocking part of firefox but also that same click activates the File submenu, that is the click registers besides making the window active.

On OSX this is different. The click do brings the window to the front, but it doesn't register. In Gnome (and KDE and Windows), if instead of the File menu I clicked on a cancel or delete button by accident that would be a bad thing and it forces me to look for a "safe" spot on the window to bring it to the front. On OSX this is not a concern.

I hope I made myself clear... if not feel free to ask again :)

---

### Post by ajgreeny on 2009-08-24
OK, I see what you mean now, and to be honest, it's something that I wasn't even aware of, I usually click on the window list buttons in the panel to move from window to window.  I must search further as it could be useful.

---

### Post by mcduck on 2009-08-24
> **KLineD said:**
> For some time I used OSX Leopard. One feature I did like was the "click to make window active". The reason I like it is that I don't need to find a safe area to click in order to make some window active.

I've tried to get the same in Gnome, but no luck so far. I'm sorry if this has been asked before (I searched the forums, couldn't find anything).

Is there a setting in gconf or a tweak that can enable this type of behavior in Gnome?

Thanks in advance!

the "feature" that annoys me the most in OS X.. :D

Anyway, if I understood right you don't actually want to disable/enable the "click to focus"-behavior but instead disable input on non-focused windows.. I don't think there's any option for that, I've never seen one.

Maybe you could try completely different approach, and enable mouse focus, perhaps with auto raise enabled? (this wold mean that the window under mouse cursor is always active, and will raise to top after certain timeout).

edit: You could also use middle click to select your windows, most programs don't do anything with middle-click, and middle-click on buttons is ignored..

---

### Post by macogw on 2009-08-24
GNOME can't do this (it only operates Windows-style in this regard), but KDE can. In KDE you'd tell it not to pass the click through.  On KDE you'd go to System Settings -> Window Behavior -> Window Actions -> Left Button: Activate & Raise

The only workaround I can think of for GNOME would be to use focus on hover (ie. focus follows mouse) so that clicking is not required to activate a window.  Just put your mouse on it, and it becomes active so that clicking is reserved *only* for clicking buttons.

Just like mcduck, this not-passing-clicks-through behaviour on OSX drives me insane.

---

### Post by KLineD on 2009-08-24
Too bad Gnome can't do this, and I was never a fan of focus follow mouse.

Thanks for the info for doing this in KDE, maybe I'll give KDE 4.2 a shot.

---

