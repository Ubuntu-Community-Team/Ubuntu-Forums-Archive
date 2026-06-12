---
title: "[SOLVED] Anyway to improve kmenu editor?"
date: 2007-11-19
forum: Desktop Environments
---

### Post by keyboardashtray on 2007-11-19
Is there any additional program or tweak so that I could get my Kmenu editor to act, well, more like the menu editor in Gnome did?

I liked being able to check and uncheck things, so that I can take something off of the menu without forgetting I have it, or having to remember the command and icon set if I decide to put it back on.

With Kmenu editor it's either in the main menu or gone completely. I did some initial cleaning and deleted some things, like the Kubuntu nerfed version of Adept and Control Center. I know there are ways to get the default back, I'm wondering if there is some extra program to get more out of it, or if anyone knows if KDE will ever improve this?

---

### Post by samwyse on 2007-11-19
You can hide items by putting a dot in front of the item name. Maybe KDE4 will have a more advanced way to hide menu items.

I dump items I don't need to access in a submenu.

---

### Post by keyboardashtray on 2007-11-19
Great! Except, I tested it with my Games menu, and now when I bring up the kmenu editor, it's not in there either. 

How do I show the hidden files?

---

### Post by samwyse on 2007-11-19
Sorry, apparently it doesn't work the same way for submenus. Go to .local/share/desktop-directories and open Games.directory file in a text editor and remove the dot from the name and save. Start the menu editor and save menu. Then restart the menueditor. The menu should be back.

---

### Post by keyboardashtray on 2007-11-19
Thank you, that brought it back! The reason I tried hiding the whole directory, was at first, adding a . in front of a specific entry didn't hide it - but when I added it to the description it did. I bet that is because I have it set up to list items as Description (Program Name) instead of Program Name (Description) maybe?

But anyhow, thanks for the tips! This will help clean up a ton. I will also try your suggestion of a sub directory for the less often used stuff. I knew about . for hidden files in a file browser, didn't know they applied to the menu entries too. This will definitely be sufficient for what I need, but it would be interesting to see KDE take a page from Gnome's books on the main menu handling.

---

### Post by samwyse on 2007-11-19
> **keyboardashtray said:**
> I bet that is because I have it set up to list items as Description (Program Name) instead of Program Name (Description) maybe?

That must be it, because I'm just using program names.

---

