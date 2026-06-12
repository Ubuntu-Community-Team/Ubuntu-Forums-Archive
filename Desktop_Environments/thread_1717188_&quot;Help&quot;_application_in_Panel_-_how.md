---
title: "&quot;Help&quot; application in Panel - how?"
date: 2011-03-29
forum: Desktop Environments
---

### Post by Chosulman on 2011-03-29
The "Help" application icon (a lifebelt) was in the top panel until I accidentally removed it.

How do I get "Help" back onto the top panel, please?

Ubuntu 10.04 LTS + Gnome Desktop, fresh install.  Asus EeePC 1000H
-----------------------------------------------------------------------------------------------------------
Yes, I have scoured the forums.  Yes, I have read "Help" both on the machine and on-line.   Yes,
I have studied various recent Ubuntu books.  Yes I have hacked for several hours.  I can do /anything/
normal with panels - EXCEPT get the "Help" application onto one.

Hoping for some enlightenment ...

---

### Post by Krytarik on 2011-03-29
It's weird that it's that hard to get the default "Help" launcher back. However, I finally figured it out, here it is:

1.) add a usual custom launcher:
- right-click at the panel
- choose "Add to Panel..."
- select "Custom Application Launcher"
- click at "Add"
- enter "yelp" into both fields "Name" and "Command"
- confirm with "OK", then "Close"

2.) Here comes the real part:
- press Alt+F2
- launch gconf-editor:
```
gconf-editor /apps/panel/objects
```- select the very last object
- replace "yelp.desktop" with "/usr/share/applications/yelp.desktop" as value for the key "launcher_location"

3.) remove the created desktop-file (just to clean up):
```
rm ~/.gnome2/panel2.d/default/launchers/yelp.desktop
```4.) restart gnome-panel:
- press Alt+F2
- enter:
```
killall gnome-panel
```Greetings.

---

### Post by wojox on 2011-03-29
Open your menu, click and drag it back up there.

---

### Post by Krytarik on 2011-03-29
> **wojox said:**
> Open your menu, click and drag it back up there.
OMG, this is just great! Couldn't you have come here earlier?! ;-) I didn't thought of drag-and-drop, right-clicking that item, like you can do with any other usual launcher, just runs it. The same applies to the other items of the "System" toplevel menu.

---

### Post by Chosulman on 2011-03-30
> **wojox said:**
> Open your menu, click and drag it back up there.

Thank you for your reply.  Sorry to appear dim, but which Menu are you referring to, please?

Neither 'Applications', 'Places' nor 'System' nor any of their sub-menus has the "Help" (lifebelt) application in it.

With best wishes.

---

### Post by Krytarik on 2011-03-30
You should find an item called "Help and Support" at the toplevel of the "System" menu, that's it.

Of course it has not necessarily a life belt as the icon, that depends on your chosen icon theme. For me, it's an encircled question mark, I'm using the AwOken icon theme.

---

### Post by Chosulman on 2011-03-30
> **Krytarik said:**
> You should find an item callded "Help and Support" in the toplevel of the "System" menu, that's it.

Of course it has not necessarily a life belt as the icon, that depends on your chosen icon theme. For me, it's an encircled question mark, I'm using the AwOken icon theme.

Thank you!  That worked.

But ... there is no icon beside the text "Help and Support" in the System menu.  In fact there are no icons at all in that menu ... can they somehow be installed?   I'm using the default theme 'Ambiance', exactly as supplied outa-the-box.

I guess this illustrates one of the major problems with Ubuntu (and most contemporary GUIs) - the lack of a "Style Guide" to encourage consistent interface design across applications and related elements.  Such is life.

Thank you for your time, and /very/ prompt, helpful responses.

---

### Post by mcduck on 2011-03-30
> **Chosulman said:**
> Thank you!  That worked.

But ... there is no icon beside the text "Help and Support" in the System menu.  In fact there are no icons at all in that menu ... can they somehow be installed?   I'm using the default theme 'Ambiance', exactly as supplied outa-the-box.

I guess this illustrates one of the major problems with Ubuntu (and most contemporary GUIs) - the lack of a "Style Guide" to encourage consistent interface design across applications and related elements.  Such is life.

Thank you for your time, and /very/ prompt, helpful responses.

Actually the lack of those icons is *exactly because* there is a style guide that says there shouldn't be icons. :D

In this case it's the [Gnome Human Interface Guidelines]("http://library.gnome.org/devel/hig-book/stable/") that demands that menu icons should only be used for selected, more important, menu items and not for every menu entry, to bring the user's attention to those important items and to reduce visual clutter in the menus.

So blaming the lack of design guidelines is wrong here, and so is  blaming Ubuntu. ;)

(if you want to have the icons for every menu item that can be enabled though gconf-editor, just enable the *desktop/gnome/interface/menus_have_icons* -key.)

edit: The menus used to have icons everywhere, but that was removed in Gnome 2.28 and later:
> GNOME menus and buttons have been standardised across all applications to not display icons by default. Menu items with dynamic objects, including applications, files or bookmarks, and devices are the exception and can display an icon. This change will standardise the look and feel of menus and present a cleaner interface to users.
[http://library.gnome.org/misc/release-notes/2.28/]("http://library.gnome.org/misc/release-notes/2.28/")

---

### Post by Chosulman on 2011-03-30
> **mcduck said:**
> Actually the lack of those icons is *exactly because* there is a style guide that says there shouldn't be icons. 

Thank you for the clarification about Style.

Dragging a line of *text* out of a Menu onto a panel is hopelessly counter-intuitive.  Had there been an *icon* on that same menu entry, I would have had no inhibitions about dragging it about, if only to see what would happen - which would have been the appearance of the same icon on the panel.  A discoverable feature; a reasonable outcome in a GUI paradigm.

The solution of dragging the text line out of the System menu is not described in the Help documentation "Desktop User Guide / Using the Panels / Panel Objects / Adding an Object to A Panel".

Anyway, we have a result, and I propose to mark this item as "solved".  A remarkable forum, and many thanks to all.  :KS

---

