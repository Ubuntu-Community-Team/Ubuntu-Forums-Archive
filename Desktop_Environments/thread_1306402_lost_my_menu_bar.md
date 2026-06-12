---
title: "lost my menu bar??"
date: 2009-10-30
forum: Desktop Environments
---

### Post by audience of one on 2009-10-30
I did something and now I don't have the kde menu bar accross the bottom.  How do I get it back?

I have a button at the top left that shows the "K" icon.

Todd

---

### Post by v41 on 2009-10-30
> **audience of one said:**
> I did something and now I don't have the kde menu bar accross the bottom.  How do I get it back?

I have a button at the top left that shows the "K" icon.

Todd

Activate the KRunner window (Alt-F2) and enter,
```

plasma-desktop --nocrashhandler

```

---

### Post by audience of one on 2009-10-30
> **v41 said:**
> Activate the KRunner window (Alt-F2) and enter,
```

plasma-desktop --nocrashhandler

```

That didn't make any noticeable change.

---

### Post by v41 on 2009-10-30
> **audience of one said:**
> That didn't make any noticeable change.
OK, it sounds as though plasma-desktop is running but has lost track of the panel.    If you right-click on the desktop,
a menu should appear.  Try selecting the "add panel" menu item and see whether that helps.

---

### Post by Marrkk on 2009-10-31
add a panel ...
not sure if its in folder view or desktop view,
 non karmic KDE;s plasma crashed occasionally, 
so u have to re add the widget / panel to the desktop,
but u only see the add new panel in one viewmode, prob folder view mode..
so right-click and check a few options out, u should be good to go.
then u will prob have to manually add 
App launcher - task manager - system tray - clock = battery / power
widgets back..
the order which u add these matters too, work from the left to right..
hth

---

### Post by audience of one on 2009-11-02
> **Marrkk said:**
> add a panel ...
not sure if its in folder view or desktop view,
 non karmic KDE;s plasma crashed occasionally, 
so u have to re add the widget / panel to the desktop,
but u only see the add new panel in one viewmode, prob folder view mode..
so right-click and check a few options out, u should be good to go.
then u will prob have to manually add 
App launcher - task manager - system tray - clock = battery / power
widgets back..
the order which u add these matters too, work from the left to right..
hth

Maybe I haven't stated the issue very well, but I now have a floating menu, want it fixed at the bottom of the screen.  does that make sense?

---

### Post by mrboojive on 2009-11-02
Yes. You need to add a panel so you can put the menu on the panel. Make sure widgets are unlocked, then right click on the desktop and add a panel. Then drag your floating menu to the panel.

---

### Post by audience of one on 2009-11-02
> **mrboojive said:**
> Yes. You need to add a panel so you can put the menu on the panel. Make sure widgets are unlocked, then right click on the desktop and add a panel. Then drag your floating menu to the panel.

That did it.  Sorry to all that am slow to get this. :)

---

### Post by TheFug on 2009-11-29
Had same problem on gOS with iBar, my solution: enter the iBar configuration, and do a "refresh" and the bar returns on the desktop.

---

