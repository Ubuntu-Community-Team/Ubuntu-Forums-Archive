---
title: "gtkrc panel menu items different from application menu items"
date: 2007-10-12
forum: Desktop Environments
---

### Post by wanchai on 2007-10-12
In my gnome panel I have a Main Menu (MS calls this Start Menu), a Window Selector and a bunch of other stuff. Now I'd like to color the items in the main menu and windows selector in a different way than the menu items of regular applications.

I know that I can color the menu bar of an application with
[FONT="Courier New"][COLOR="Navy"]   class "GtkMenu" style "redish"[/COLOR][/FONT]

And the lines
[FONT="Courier New"][COLOR="Navy"]   widget "*PanelWidget*" style "greenish"
   widget "*PanelApplet*" style "greenish"
   class "*Panel*" style "greenish"[/COLOR][/FONT]
can be used to turn the whole gnome panel into something greenish.

But the line
[FONT="Courier New"][COLOR="Navy"]   class "GtkMenuItem" style "blueish"[/COLOR][/FONT]
will color all menu items blue, no matter whether they are part of a menu bar in an application or whether they pop up (or drop down) from the main menu in the gnome panel.

Is it possible, in general, to color the widgets of individual applications differently? And does anyone know the name of the widget or widget_class of the main menu items and window selector items so I can assign them a style that overrides the generic one?

---

