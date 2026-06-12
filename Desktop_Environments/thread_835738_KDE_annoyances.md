---
title: "KDE annoyances"
date: 2008-06-20
forum: Desktop Environments
---

### Post by diaa on 2008-06-20
A while ago I switched to KDE(3.5.x) from GNOME and I was pretty happy with KDE but I noticed some annoying things that are mostly related to window management and the taskbar, but they are not related.
I'll list them hoping that someone can help me fix them:
1- Flashing windows in other desktops(other than the current) don't appear and there's no way to tell that a window in another desktop requires attention.
[I]In GNOME, this used to happen as follows, a window flashing in another desktop appears in the current desktop taskbar as a normal flashing window and as soon as you click it the desktop is switched to that of the flashing window and it gets focus.
[/I]2- Flashing windows don't show hidden panels/the taskbar, when you set the panel to auto-hide, a flashing window doesn't make it show and consequently you never know a window is flashing until you unhide the panel for some reason or another.
3- After showing the desktop, using the button on the panel, any new window makes all the minimized applications appear.

I thought about using *fbpanel* to solve 1, 2 and I gave it a quick run but it doesn't fix 1, didn't test 2 because I didn't set it to auto-hide.

so what are your thoughts?

---

### Post by Happy_Man on 2008-06-20
1- Right click on the panel and click configure, there is an option somewhere in there to display alerts/windows from all desktops, can't get it for you right now, as I don't have KDE installed, but it's there. 

2 - That's not a bug, that's a feature! :p

3 - Not sure.

---

### Post by diaa on 2008-06-22
Thanks for your comments

> **Happy_Man said:**
> 1- Right click on the panel and click configure, there is an option somewhere in there to display alerts/windows from all desktops, can't get it for you right now, as I don't have KDE installed, but it's there. 


There's an option there that says "Show windows from all desktops" but it's not convenient since I usually have ~4-8 windows in each of my 3 desktops, I couldn't find another option specific to the alerts.

> **Happy_Man said:**
> 
2 - That's not a bug, that's a feature! :p


I don't see this as a feature... I mean how can hiding an alert from the user be a feature? is there anyway to disable it?

> **Happy_Man said:**
> 
3 - Not sure.
It's easy to reproduce, go to an empty desktop, open any application, click show desktop then open another application, in case the new application is not maximized or hiding the previous application window you'll easily see that the first application has been restored.

---

### Post by Zorael on 2008-06-22
> **diaa said:**
> 1- Flashing windows in other desktops(other than the current) don't appear and there's no way to tell that a window in another desktop requires attention.
*In GNOME, this used to happen as follows, a window flashing in another desktop appears in the current desktop taskbar as a normal flashing window and as soon as you click it the desktop is switched to that of the flashing window and it gets focus.*
> **diaa said:**
> 2- Flashing windows don't show hidden panels/the taskbar, when you set the panel to auto-hide, a flashing window doesn't make it show and consequently you never know a window is flashing until you unhide the panel for some reason or another.
These are more of wishlist-type things. Perhaps posting it as such can get them included into KDE4. I keep my kicker bar at size ~56, so the taskbar panel fits three rows of entries, minimizing windows having to contend for the space. As for urgent windows, you can set a sound effect to blare when a window wants attention in Notifications -> System Notifications -> Event source: The KDE Window Manager -- and a keybind to Activate Window Demanding Attention in Keyboard & Mouse -> Keyboard shortcuts.

> **diaa said:**
> 3- After showing the desktop, using the button on the panel, any new window makes all the minimized applications appear.
This is also per design; 'show desktop' doesn't equate to 'minimize all'. Looking through the available keybinds I don't see such an option, either.

---

