---
title: "So when will KDE4 be mature?"
date: 2009-12-07
forum: Desktop Environments
---

### Post by apmcd47 on 2009-12-07
We're on what, 4.3? And yet:
[LIST]
[*]Your wallpaper is common to all desktops
[*]Panels **HAVE **to be added bottom-top-left-right
[*]You cannot add a launcher to a panel which is not already in your menu
[*]Buttons on the panel cannot be positioned
[*]You cannot set Window Manager short cuts, e.g., to raise/lower windows
[*]All the documentation is for KDE 3.x!
[/LIST]
Sheesh!

Andrew

---

### Post by Zorael on 2009-12-08
You can too have different wallpapers on different desktops. Or rather, you can have independent activities on each, which by extension means independent wallpapers and plasma widget setups. Hit the cashew, zoom out, Configure Plasma, check Different activity for each desktop.

Panels have to be attached to a screen edge, yesh.

You can too add launchers to your panel without them first existing in the menu, but they must exist *somewhere* first. Meaning, you must have a .desktop file created to drag onto the panel. If you create a directory someplace, and then in it create your launchers (such as via Dolphin, right click, Create New -> Link to Application), you can then drag them to your panel(s) as you please.

KWin has a bunch of keyboard shortcuts you can set, including raise/lower, maximize/restore, minimize, set sticky, move window/user to desktop left/right/up/down/[n], activate urgent window, shade window, etc. System Settings -> Keyboard and Mouse -> Global Keyboard Shorcuts. Like where all global shortcuts are kept. Perhaps you were looking in the wrong place, or missed the scrolldown menu to change shortcut component.

But yeah, documentation is old.

---

### Post by apmcd47 on 2009-12-08
> **Zorael said:**
> You can too have different wallpapers on different desktops. Or rather, you can have independent activities on each, which by extension means independent wallpapers and plasma widget setups. Hit the cashew, zoom out, Configure Plasma, check Different activity for each desktop.
Okay, start from basics - WTF is a cashew? Is it that ugly gnome-footprint thing in the top right corner? All the above to replace a radio button?
> **Zorael said:**
> 
Panels have to be attached to a screen edge, yesh.
That's not what I have a problem with. My problem is with the fact that to get one on the left edge I have to create one on the top **then** one on the left edge. And then I need to delete one! All for the want of a submenu saying "top bottom left right".
> **Zorael said:**
> 
You can too add launchers to your panel without them first existing in the menu, but they must exist *somewhere* first. Meaning, you must have a .desktop file created to drag onto the panel. If you create a directory someplace, and then in it create your launchers (such as via Dolphin, right click, Create New -> Link to Application), you can then drag them to your panel(s) as you please.
Isn't that a KDE2 trick that you no longer needed in KDE3? In other words, a retrograde step?

And it's not obvious that you can do that.
> **Zorael said:**
> 
KWin has a bunch of keyboard shortcuts you can set, including raise/lower, maximize/restore, minimize, set sticky, move window/user to desktop left/right/up/down/[n], activate urgent window, shade window, etc. System Settings -> Keyboard and Mouse -> Global Keyboard Shorcuts. Like where all global shortcuts are kept. Perhaps you were looking in the wrong place, or missed the scrolldown menu to change shortcut component.

No, I'd found the right place but looking there now I found there is a KDE component menu which was usefully set to kmix, so I thought that was all I could change. Thanks for making me **look!**
> **Zorael said:**
> But yeah, documentation is old.
They could at least put a message at the top of the documentation telling you it's for KDE3.

Another thing missing is the window list on the middle mouse button. Very useful for going quickly not only to **a** window, but a particular window on a particular desktop. I forgot that in my first post. 

Andrew

---

### Post by Zorael on 2009-12-08
> **apmcd47 said:**
> Okay, start from basics - WTF is a cashew? Is it that ugly gnome-footprint thing in the top right corner? All the above to replace a radio button?
[Cashews](http://en.wikipedia.org/wiki/Cashew). [Picture](http://en.wikipedia.org/wiki/File:CashewSnack.jpg). :3

> **apmcd47 said:**
> That's not what I have a problem with. My problem is with the fact that to get one on the left edge I have to create one on the top **then** one on the left edge. And then I need to delete one! All for the want of a submenu saying "top bottom left right".
Wait, what? Try unlocking widgets, clicking the panel cashew, clicking and holding Screen Edge and then drag it to the edge you want it to attach to.

> **apmcd47 said:**
> Isn't that a KDE2 trick that you no longer needed in KDE3? In other words, a retrograde step?

And it's not obvious that you can do that.
It's difficult to add both launchers and "drawers", as in folders with more icons in them. Both can be done, but they require manually making directories and .desktop files elsewhere. IIRC, in KDE3 you could just right-click and Create Launcher, but that functionality seems to have yet to hit KDE4.

---

### Post by llawwehttam on 2009-12-08
This is why I use Gnome!

---

### Post by apmcd47 on 2009-12-08
> **Zorael said:**
> [Cashews](http://en.wikipedia.org/wiki/Cashew). [Picture](http://en.wikipedia.org/wiki/File:CashewSnack.jpg). :3
Nuts is what I thought in the first place. The thing in the corner still looks like a deformed gnome footprint.
So I click on the footprint and select "Zoom Out". Then I click on "Create New Activity" and then on the spanner to change the background. Then what? I don't see a "Configure Plasma" option.

> **Zorael said:**
> 
Wait, what? Try unlocking widgets, clicking the panel cashew, clicking and holding Screen Edge and then drag it to the edge you want it to attach to. First thing I tried. I ended up having to create a second one and delete the first.



Andrew

---

### Post by Zorael on 2009-12-08
See attachments.

---

### Post by apmcd47 on 2009-12-08
Thanks for that - a grab widget cunningly disguised as a regular button, eh? Who would have thought of that? If you click on it it brings up some size gadgets, doesn't it?

When I found my menu didn't look like yours in the picture I checked the version of KDE. As it's a recently released distro (not Ubuntu - this is work-related) I expected it to have KDE 4.3 or later - actually it's 4.2.4! :cry:

One thing I have discovered: Right-click on the K menu and you can change it to the "traditional" menu format :twisted:

And I don't care what anyone else calls that thing - it still looks like a deformed Gnome Footprint to me - maybe that's deliberate?:razz:

Andrew

---

### Post by SunnyRabbiera on 2009-12-08
Well truth be told KDE4 is not at its best in Ubuntu, but it is very good in openSUSE 11.2 and Mandriva 2010.0

---

### Post by aveightor on 2009-12-08
[http://www.kde.org/documentation/](http://www.kde.org/documentation/)  kde4 manual

[http://docs.kde.org/](http://docs.kde.org/)

---

### Post by jrusso2 on 2009-12-08
Seems like since 4.2.4 its been pretty mature for me.

---

### Post by Zorael on 2009-12-09
> **apmcd47 said:**
> Another thing missing is the window list on the middle mouse button. Very useful for going quickly not only to **a** window, but a particular window on a particular desktop. I forgot that in my first post.

The only semi-equavilence I've found is the window list plasma widget. It's in the repositories as **plasma-widget-windowlist**. You can put it on the panel or on the desktop, and then either click it or bind a key to it. I imagine the middle-click button won't work, though, but a keyboard shortcut will.

---

### Post by quazi on 2010-01-06
Is it as of yet possible to customize the desktop right-click menu in KDE4?  This was really easy in KDE3.5 and it's pretty incredible that this doesn't seem possible in KDE4.

---

### Post by Zorael on 2010-01-07
> **quazi said:**
> Is it as of yet possible to customize the desktop right-click menu in KDE4?  This was really easy in KDE3.5 and it's pretty incredible that this doesn't seem possible in KDE4.
Some basic support for this is in the 4.4 betas.; see attached screenshots for an idea of how it looks in 4.4.b2.

You grab mouse events much like you normally do when setting up keybinds, and then you set what it should do. And as the second one shows, there are other choices than having it spawn a menu. I'm not sure why anyone would want Paste, but hey. :3

---

### Post by Zorael on 2010-01-08
As a follow up;
> **apmcd47 said:**
> Another thing missing is the window list on the middle mouse button. Very useful for going quickly not only to **a** window, but a particular window on a particular desktop. I forgot that in my first post.
This functionality is provided by the "Switch window" action visible in one of the screenshots in my previous post.

Also, "Application Launcher" pops up a KDE3 Kicker-like application menu.

---

