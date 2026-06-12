---
title: "Why Can't I Get Rid of Those Gnome Menu Icons Anymore?"
date: 2010-05-21
forum: Desktop Environments
---

### Post by NotPhil on 2010-05-21
I just upgraded to Lucid Lynx from Hardy Heron and discovered that I could no longer remove menu and button icons through the Appearance Preferences.

After a little research I found a similar setting in gconf-editor (buttons_have_icons and menus_have_icons, both now unchecked), which works for everything except the Gnome Main Menu and Firefox.

I eventually found [a way to get rid of menu icons in Firefox]("http://www.ghacks.net/2009/05/11/how-to-remove-favicons-in-firefox-bookmarks/"), but can't find any information on how to get rid of them in the Gnome Main Menu.

Does anyone know how to do this, or, if not, does anyone know when Gnome will be fixing this bug?

---

### Post by Frogs Hair on 2010-05-22
The only way I know of is to un-check  the boxes from the main menu under preferences. To delete items click on the item
and select delete from the right side of the main menu.

---

### Post by NotPhil on 2010-05-23
> **Frogs Hair said:**
> The only way I know of is to un-check  the boxes from the main menu under preferences.Thanks for replying, but I wanted to remove the menu icons, not the menu items.

Apparently, someone decided to hard-code the icon-display function in the Gnome Main Menu after some users got ticked-off when Gnome made no-icons-in-menus the default setting.

The only way around this I've found is to download the Gnome Color Chooser, click on the Icons tab, and make the icons one pixel in size. They're still there, but they're barely noticeable.

Someone really should fix this so users can choose between menu icons or no menu icons without having to use a kludge like this.

---

### Post by andy.thornton on 2010-08-25
I would love to see this fixed, I run Lucid on my netbook and removing the icons frees up a lot of screen real estate.

---

